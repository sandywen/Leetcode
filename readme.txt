141.Link list Cycle
1.one_step 一次走一步，two_step 一次走两步
2.如果link list有环，那么one_step和two_step一定会相遇，因为two_step会在环上一直循环
3.如果link list无环，那么one_step和two_step不会相遇
4.这个问题最重要的是while循环里非空的判断条件，我刚开始写的是one_step.next !=null && two_step.next.next !=null就会一直报nullpoint的错，
后来才发现，我写错了，应该是two_step.next != null && two_step.next.next != null，这样就对了。因为如果two_step.next=null的时候，two_step.next.next执行的时候就会出现null.next就报nullpoint的错了。