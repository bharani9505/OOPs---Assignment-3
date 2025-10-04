# OOPs---Assignment-3
package TASK;
	class MyThread extends Thread {
	    public void run() {
	        System.out.println("Thread started...");
	        for (int i = 1; i <= 10; i++) {
	            if (Thread.currentThread().isInterrupted()) {
	                System.out.println("Thread was interrupted! Stopping execution...");
	                return;
	            }
	            System.out.println("Count: " + i);
	            try {
	                Thread.sleep(1000); 
	            } catch (InterruptedException e) {
	                System.out.println("Thread interrupted during sleep!");
	                Thread.currentThread().interrupt(); 
	            }
	        }
	        System.out.println("Thread completed normally.");
	    }
	}
  public class ThreadInterruptDemo {
	    public static void main(String[] args) {
	        MyThread t1 = new MyThread(); 
	        t1.start(); 
	        try {
	            Thread.sleep(3000); 
	        } catch (InterruptedException e) {
	            e.printStackTrace();
	        }
	        System.out.println("Main thread is interrupting the child thread...");
	        t1.interrupt(); 
	    }
	}
