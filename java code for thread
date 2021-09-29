package sample;

class Calc1
{
	int i,j;
	public int add()
	{
		return i+j;
	}
}
//child thread!
class CalcService implements Runnable
{
	Calc1 obj1;//Object of Calc1 class!
	int a[];
	int b[];
	public CalcService(Calc1 obj1, int[] a, int[] b) 
	{
		super();
		this.obj1 = obj1;
		this.a = a;
		this.b = b;
	}
	@Override
	public void run() 
	{
		try
		{
			System.out.println("Thread:: "+Thread.currentThread());
			
			synchronized(obj1)//class Calc1 Object  
			{
			for(int i=0;i<a.length;i++)
			{
				obj1.notify();
				
				obj1.i=a[i];//t1 thread
				obj1.j=b[i];//t2 thread
				System.out.println(a[i]+ " "+b[i]);
				System.out.println("Thread:: "+Thread.currentThread()+ " "+obj1.add());//a[i]+b[j]
				obj1.wait();
			}
			obj1.notifyAll();//final notification to main thread
			}
		}
		catch(Exception e)
		{
			e.printStackTrace();
		}
		System.out.println("Child Thread Over!");

	}

}
public class InterThreadCommunication {

	public static void main(String[] args)throws Exception
	{
		Calc1 c=new Calc1();
		CalcService s1=new CalcService(c,new int[]{11,21,31,41,51},new int[]{1,2,3,4,5});
		CalcService s2=new CalcService(c,new int[]{2,2,2,2,2},new int[]{10,20,30,40,50});
		
		Thread t1=new Thread(s1);
		Thread t2=new Thread(s2);
		t1.start();
		t2.start();
		t1.join();
		t2.join();
		System.out.println("Main Thread Over!");

	}



}
