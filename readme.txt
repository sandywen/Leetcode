2.Add Two Numbers
1.首先，我没弄清楚题目的意思，而且他给的例子有歧义。比如342+465=807，而243+564=807。
2.弄清题意之后，我明白了，实际上对每位相加，如果大于10就往前进1位，用/10和%10就能够表示
3.但有些边界条件我没有想到，输入为[1]和[9,9]时，如果剩余的位数直接将9+carry(表示进位)的话，结果变成了[0,10]肯定是不对的
4.还有我输出的结果会有[8,1,0]，就是在进入while的时候会先new一个next，如果刚好两个list长度相同的话，就会多了一个为0的nextnode

141.Link list Cycle

1.one_step 一次走一步，two_step 一次走两步
2.如果link list有环，那么one_step和two_step一定会相遇，因为two_step会在环上一直循环
3.如果link list无环，那么one_step和two_step不会相遇
4.这个问题最重要的是while循环里非空的判断条件，我刚开始写的是one_step.next !=null && two_step.next.next !=null就会一直报nullpoint的错，后来才发现，我写错了，应该是two_step.next != null && two_step.next.next != null，这样就对了。因为如果two_step.next=null的时候，two_step.next.next执行的时候就会出现null.next就报nullpoint的错了。

160. Intersection of Two Linked Lists
1.我做题的时候首先想到了本科的一种方法，就是先遍历两个链表得到他们的长度分别为m和n，先走到长链表，到达和短链表长度相同的位置，然后一起遍历两条链表，如果有两个listnode相同的话，就存在着相同点，否则不存在；
2.其他人做的更简洁的方法是，遍历长链表和短链表两边，如果他们有共同点，一定会相遇。因为他们最终都会走m+n步，有相同点的话一定走相同步数到共同点然后最后一起到达终点。两个指针分别将两个链表遍历一遍。

203. Remove Linked List Elements
1.如果使用if(cur.val == val) cur.val = cur.next.val; cur.next = cur.next.next; 最后一个listnode如果等于val会没有办法删除，因为cur.next = null时就跳出了循环
2.使用if(cur.next.val == val) cur.next = cur.next.next;如果这样第一个node没有遍历到，最后检查第一个listnode是否等于val，如果等于返回head.next

234. Palindrome Linked List
1.判断是否为回文，我先开始想错了，我刚开始想的是找到链表的中点，然后从开始位置和中点开始遍历看他们相等。这不是回文。后来又想到将链表逆置对比两条链表的值是否相等，发现这个空间复杂度不是o(1)，需要新建一条链表，不然的话就会一直报错，因为head的next已经改为null了，不能通过遍历head和rhead来得到结果。
2.想法是找到链表的中点，通过s和f两个指针，s每次走一步，f每次走两步。对于链表长度为偶数，s刚好是回文下半部分的第一个数，f指向null；长度为奇数，s是回文中点，f指向最后一个listnode。想法是将另一半的字符逆转，然后比较两部分字符是否相同。长度为奇数是，s需要往下走一步，通过f是否为null来判断。