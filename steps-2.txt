1)fork the branch
2)run test
3)it hungs
4)check changes
5) there is some strange for 72000 + wait(1000) - try to speed up
6) looks like the method is called many times. 
7) I don't see logic in this code.
private void validate() throws IllegalArgumentException {
        for (int i=0; i<20*60*60; i++) {
            System.out.print('.');
            try {
                Thread.currentThread().sleep(1000);
            } catch (InterruptedException e) {
                break;
            }
        }
8) works without above code.
