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