# ck
public class Xuancaipiao {
public static void main(String[] args) {
	System.out.println("请输入：红球个数 红球号码范围 蓝球个数 蓝球号码范围");
	Scanner b=new Scanner(System.in);
	int red = b.nextInt();
	int rs=b.nextInt();
	int blue=b.nextInt();
	int bs=b.nextInt();
Xuancaipiao x=new Xuancaipiao();
for(int i=0;i<5;i++) {
	int [] a=x.choosenumber(red, rs, blue, bs);
	System.out.println(Arrays.toString(a));
	x.lucky(rs);
	System.out.println();
	x.lucky(bs);
	System.out.println();
	}
}
int[] choosenumber(int red,int rs,int blue,int bs){
	int n=red+blue;
	int[] a=new int[red+blue];
	
	for(int i=0;i<red;i++) {
		a[i]=(int)(Math.random()*rs+1);
		for(int j=0;j<i;j++) {
			if(a[j]==a[i]) {
				i=i-1;
			}
		}
	}
	for(int i=0;i<blue;i++) {
		a[red+i]=(int)(Math.random()*bs+1);
		for(int j=red;j<red+blue-1;j++) {
			if(a[j]==a[i]) {
				i=i-1;
			}
		}
	}
	for(int j=0;j<red-1;j++){
	for(int i=0;i<red-1-j;i++) {
		if (a[i]>a[i+1]) {
			int temp=a[i+1];
			a[i+1]=a[i];
			a[i]=temp;
		}
	}
	}
	return a;
}
void lucky(int scope) {
	long []a=new long[scope+1];
	for(long i=0;i<21425712;i++) {
		a[(int)(Math.random()*scope+1)]=a[(int)(Math.random()*scope+1)]+1;
	}
	int []b=new int[scope];
	for(int i=0;i<scope;i++) {
		int max=0;
		for(int j=1;j<scope+1;j++) {
			if(a[max]<a[j]) {
				max=j;
			}
			
		}
		b[i]=max;
		System.out.print(a[max]+" ");
		a[max]=-1;
	}
	System.out.println();
	for(int i=0;i<scope;i++) {
		System.out.print(b[i]+" ");
	}
}
}
