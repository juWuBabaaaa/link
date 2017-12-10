# link
//java单链表 用到了内部类  包括向链表中加入和转为对象数组两个操作


class Link 
{
	private class Node
	{
		private Object data ;
		private Node next ;
		public Node(Object data) {
			this.data = data ;
		}

		public Object getData() {
			return this.data ;
		}
		public Node getNext() {
			return this.next ;
		}
		public void addNode(Node newNode) {
			if (this.next == null)
			{
				this.next =newNode ;
			} else {
				this.next.addNode(newNode) ;
			}
		}
		public void toArrayNode() {
			Link.this.retData[Link.this.foot ++] = this.data ;
			if (this.next != null)
			{
				this.next.toArrayNode() ;
			}
		}
		public boolean containsNode(Object search) {
			if (search .equals(this.data))
			{
				return true ;
			} else {
				if (this.next != null)
				{
					return this.next.containsNode(search) ;
				} else {
					return false ;
				}
			}
		}
		public Object getNode(int index) {
			if (Link.this.foot ++ == index)
			{
				return this.data ;
			} else {
				this.next.getNode(index) ;
			}
			return null ;
		}
	}
	// ---------------------- 以下为Link类定义 ----------------------//
	private Object [] retData ;
	private int foot = 0 ;
	private Node root ;
	private int count = 0 ;
	public Node getNode() {
		return this.root ;
	}
	public void add(Object data) {
		if (data == null)
		{
			return ;
		}
		Node newNode = new Node(data) ;   //封装
		if (this.root == null) 
		{
			this.root = newNode ;
		} else {
			this.root.addNode(newNode) ;
		}
		this.count ++ ;
	}
	public int size() {
		return this.count ;
	}
	public boolean isEmpty() {
		return this.root == null && this.count == 0 ;
	}
	public Object [] toArray() {
		if (this.count == 0)
		{
			return null ;
		}
		// 开辟指定长度的数组
		// 该数组一定要交给Node类进行处理
		this.retData = new Object[this.count] ;
		this.foot = 0 ;
		this.root.toArrayNode() ;
		return this.retData ;
	}
	public boolean contains(Object search) {
		if (search == null || this.root == null)
		{
			return false ;
		}
		return this.root.containsNode(search) ;
	}
	public Object get(int index) {
		if (index >= this.count)
		{
			return null ;
		}
		this.foot = 0 ;
		return this.root.getNode(index) ;
	}
}
public class TestLinkDemo
{
	public static void main(String args[]) throws Exception {
		Link link = new Link() ;
		link.add("hello") ;
		link.add(34) ;
		link.add(true) ;
		System.out.println(link.size()) ;

		Object result [] = link.toArray() ;
		for (int x = 0; x < result.length ; x ++ )
		{
			System.out.println(result[x]) ;
		}
		System.out.println("================") ;
		System.out.println(link.get(0)) ;
		System.out.println(link.get(1)) ;

	}
}
