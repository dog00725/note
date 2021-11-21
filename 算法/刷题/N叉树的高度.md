[N 叉树的最大深度](https://leetcode-cn.com/problems/maximum-depth-of-n-ary-tree/)

**题目：**

​	给定一个 N 叉树，找到其最大深度。最大深度是指从根节点到最远叶子节点的最长路径上的节点总数。N 叉树输入按层序遍历序列化表示，每组子节点由空值分隔（请参见示例）。

**思路：**

​	DFS或者BFS

```JAVA
	/**
	 * BFS
	 */
    public int maxDepth(Node root) {
        if(null == root){
            return 0;
        }
        Deque<Node> queue = new ArrayDeque<>();
        int depth = 0;
        queue.offer(root);
        while(!queue.isEmpty()){
            int n = queue.size();
            for(int i=0;i<n;i++){
                Node temp = queue.poll();
                if(null == temp.children || temp.children.size() == 0){
                    continue;
                }
                for(Node node : temp.children){
                    queue.offer(node);
                }
            }
            depth++;
        }
        return depth;
    }
	
	/**
	 * DFS
	 */
	public int maxDepth(Node root) {
        if(null == root){
            return 0;
        }
        int ans = 0;
        for(Node node: root.children){
            ans = Math.max(ans,maxDepth(node));
        }
        return ans + 1;
    }
```