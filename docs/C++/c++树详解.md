# 树的定义

一棵树是由n（n>0）个元素组成的有限集合，其中：

（1）每个元素称为结点（node）

（2）有一个特定的结点，称为根结点或树根（root）

（3）除根节点外，其余节点能分成m（m>=0）个互不相交的有限集合 T(0)-T(m-1)。其中的每一个子集都是一个树，这些集合被称为这棵树的子树。

如下图是一棵树：

![img](https://img-blog.csdnimg.cn/img_convert/025327e996bb4c6bbcb46d87f85a5654.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

# 树的基本概念

A. 树是由递归定义的

B. 一棵树中至少有1个结点。这个节点就是根节点，他没有前驱，其余每个节点都有且只有一个前驱节点。每个节点可以有任意个后继结点。因此，树是非线性结构，但也是有序结构。

C. 一个节点的子树个数称为这个结点的度，例如上图根节点的度为2。度为0的结点被称为叶结点；度不为0的结点被称为分支结点，根以外的分支节点称为内部结点，树中各节点的度的最大值称为这棵树的度。

D. 在用图形表示的树形结构中，对两个用线段（我们称为树枝）连接的相关联的结点，称上端结点为下端节点的父节点，反之为子节点。

E. 定义一棵树的根的层次为1，其他结点的层次等于他的父节点的层次加一。一棵树中所有节点的层次的最大值称为这棵树的深度。

F. 对于树中任意两个不同的结点，从一个结点出发一定能到达另一个结点。

G.m（m>=0）棵树的结合称为森林。

# 树的遍历

在解决问题时，常常要按照某种次序来获取树中全部节点的信息，这种操作叫做树的遍历。

A. 先序遍历 先访问根节点，然后按照左右先后顺序遍历各子树（根左右）

B. 中序遍历 先访问左子树，然后访问根，最后访问右子树（左根右）

C. 层次遍历 按层次的大笑从小到大遍历，同一层次按照从左到右的顺序。

# 二叉树基本概念

二叉树（binary tree，简称BT），是一种特殊的树，它的度是2。一个节点有两个子节点，其中左边的是左子节点，右边的是右子节点。左边的叫左子树，右边的叫右子树。

# 二叉树的性质

（1）在二叉树的第 i 层上最多有 ![img](https://img-blog.csdnimg.cn/img_convert/85e90e7cbe1747beb4c6d2bd9c699fdd.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)编辑 个结点（i>=1）

（2）深度为 k 的二叉树至多有 ![img](https://img-blog.csdnimg.cn/img_convert/794ced57b11b450dabfde32ed1a12ba0.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)编辑 个结点（k>=1）

特别的，深度为 k ，且有 ![img](https://img-blog.csdnimg.cn/img_convert/794ced57b11b450dabfde32ed1a12ba0.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)编辑 个结点的二叉树称为满二叉树。

（3）对于任意一棵二叉树，如果其叶子结点数为 ![img](https://img-blog.csdnimg.cn/img_convert/ad800775369b49b6849531ccb740f006.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)编辑，度为 2 的结点数为 ![img](https://img-blog.csdnimg.cn/img_convert/08582feb9efd43fdb39fd63c53c160ec.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)编辑 ，那么 ![img](https://img-blog.csdnimg.cn/img_convert/a9527b7984684407920b2f959a231611.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)编辑。

（4）具有 n 个结点的完全二叉树的深度为 ![img](https://img-blog.csdnimg.cn/img_convert/84862e60a7c5482e82980e8bf59d4a80.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)编辑。

# 二叉树的实现

上面我们介绍了树和二叉树，那么我们现在研究一下二叉树的实现，注意，这里默认你有一些 C++ 基础。

首先我们来创建一个二叉树结点类 BSTNode，然后在类中创建几个 BSTNode 类型的变量，值，左子节点，右子节点，父节点。

```cpp
int _key;  
BSTNode *_left;  //左子节点
BSTNode *_right; //右子节点
BSTNode *_parent;  //父节点
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)



然后我们初始化，这里使用列表初始化。

```cpp
BSTNode(int k = 0, BSTNode *l = NULL, BSTNode *r = NULL, BSTNode *p = NULL) : _key(k), _left(l), _right(r), _parent(p) {};
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

接下来，我们来创建一个二叉树类 BinaryTree ，来写二叉树的各种操作函数。

我们先声明函数

```cpp
void insert(int _key);  //将_key节点插入到二叉树中
void PreOrder();  //前序二叉树遍历
void InOrder();  //中序二叉树遍历
void PostOrder();  //后序二叉树遍历

BSTNode *search(int _key);  //递归实现，在二叉树中查找_key节点
BSTNode *IteratorSearch(int _key);  //迭代实现，在二叉树中查找_key节点

BSTNode *successor(BSTNode *x);  //找节点(x)的后继节点。即，查找"二叉树中数据值大于该节点"的"最小节点"
BSTNode *predecessor(BSTNode *x);  //找节点(x)的前驱节点。即，查找"二叉树中数据值小于该节点"的"最大节点"

void remove(int _key);  //删除_key节点

void destroy();  //销毁二叉树
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

这里包括了二叉树的基本操作。

类的private部分：

```cpp
BSTNode *_root;  //根节点
void PreOrder(BSTNode *tree); //前序二叉树遍历
void InOrder(BSTNode *tree);  //中序二叉树遍历
void PostOrder(BSTNode *tree);  //后序二叉树遍历

BSTNode *search(BSTNode *x, int _key);  //递归实现，在”二叉树x“中查找_key节点
BSTNode *IteratorSearch(BSTNode *x, int _key);  //迭代实现，在“二叉树x”中查找_key节点

BSTNode *minimum(BSTNode *tree);  //查找最小节点：返回tree为根节点的二叉树的最小节点
BSTNode *maximum(BSTNode *tree);  //查找最大节点：返回tree为根节点的二叉树的最大节点

void insert(BSTNode *&tree, BSTNode *z);  // 将节点(z)插入到二叉树(tree)中

BSTNode *remove(BSTNode *tree, BSTNode *z);  // 删除二叉树(tree)中的节点(z)，并返回被删除的节点

void destroy(BSTNode *&tree);  //销毁二叉树
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

也是声明了一些函数。

##  插入元素

```cpp
void BinaryTree::insert(int _key)  //将_key节点插入到二叉树中
{
    BSTNode *z = new BSTNode(_key, NULL, NULL, NULL);
    if (z == NULL)
    {
        return;  
    }
    insert(_root, z); 
}
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

```cpp
void BinaryTree::insert(BSTNode *&tree, BSTNode *z)  // 将节点(z)插入到二叉树(tree)中
{
    BSTNode *y = NULL;
    BSTNode *x = tree;
 
    while (x != NULL) 
    {
        y = x;
        if (z->_key < x->_key)
        {
            x = x->_left;
        }
        else
        {
            x = x->_right;
        }
    }
 
    z->_parent = y;
    if (y == NULL)
    {
        tree = z;
    }
    else
        if (z->_key < y->_key)
        {
            y->_left = z;
        }
        else
        {
            y->_right = z;
        }
}
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

首先创建一个结点，如果节点的值（key）是空（NULL）的话就结束函数，如果不为空的话就执行insert函数。insert函数的内容是循环树只要不为空，按照树的顺序找到合适的位置插入元素。

## 删除结点

```cpp
BSTNode *BinaryTree::remove(BSTNode *tree, BSTNode *z)  // 删除二叉树(tree)中的节点(z)，并返回被删除的节点
{
    BSTNode *x = NULL;
    BSTNode *y = NULL;
 
    if (z->_left == NULL || z->_right == NULL)
    {
        y = z;
    }
    else
    {
        y = successor(z);
    }
 
    if (y->_left != NULL)
    {
        x = y->_left;
    }
    else
    {
        x = y->_right;
    }
 
    if (x != NULL)
    {
        x->_parent = y->_parent;
    }
 
    if (y->_parent == NULL)
    {
        tree = x;
    }
    else
        if (y == y->_parent->_left)
        {
            y->_parent->_left = x;
        }
        else
        {
            y->_parent->_right = x;
        }
 
    if (y != z)
    {
        z->_key = y->_key;
    }
    return y;
}
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

```cpp
void BinaryTree::remove(int _key)  // 删除二叉树(tree)中的节点(z)，并返回被删除的节点
{
    BSTNode *z, *node;
    z = IteratorSearch(_root, _key); 
    if (z == _root){
        cout<<"Root can't be delete!"<<endl;
    }
    if (z != NULL && z->_parent != NULL && z != _root)
    {
        node = remove(_root, z);  
        if (node != NULL)
        {
            delete node;
        }
    }
}
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

## 销毁二叉树

```cpp
void BinaryTree::destroy(BSTNode *&tree)  //销毁二叉树
{
    if (tree == NULL)
    {
        return; 
    }
    if (tree->_left != NULL)
    {
        return destroy(tree->_left);
    }
    if (tree->_right != NULL)
    {
        return destroy(tree->_right);
    }
    delete tree;
    tree = NULL;
}
 
 
void BinaryTree::destroy()  //销毁二叉树
{
    destroy(_root);
}
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

## 完整代码

``` c++
/*
    文件创建者: 112233-星澜-imimbert
    创建日期: 2023.1.12 12:33
    功能: 二叉树
*/
#include <iostream>
using namespace std;
 
class BSTNode
{
public:
    int _key;  
    BSTNode *_left;  //左子节点
    BSTNode *_right; //右子节点
    BSTNode *_parent;  //父节点
     
    BSTNode(int k = 0, BSTNode *l = NULL, BSTNode *r = NULL, BSTNode *p = NULL) : _key(k), _left(l), _right(r), _parent(p) {};  //初始化列表
};
 
 
class BinaryTree
{
/****
    * @author 112233-imimbert-星澜
    * @since -verson: 1.0.0
    * @date 2021-01-12
    * @pre 二叉树已经创建
    * @include iostream
****/
public:
    BinaryTree();  
    ~BinaryTree();  
 
    void insert(int _key);  //将_key节点插入到二叉树中
    void PreOrder();  //前序二叉树遍历
    void InOrder();  //中序二叉树遍历
    void PostOrder();  //后序二叉树遍历
 
    BSTNode *search(int _key);  //递归实现，在二叉树中查找_key节点
    BSTNode *IteratorSearch(int _key);  //迭代实现，在二叉树中查找_key节点
 
    BSTNode *successor(BSTNode *x);  //找节点(x)的后继节点。即，查找"二叉树中数据值大于该节点"的"最小节点"
    BSTNode *predecessor(BSTNode *x);  //找节点(x)的前驱节点。即，查找"二叉树中数据值小于该节点"的"最大节点"
 
    void remove(int _key);  //删除_key节点
 
    void destroy();  //销毁二叉树
 
 
private:
    BSTNode *_root;  //根节点
    void PreOrder(BSTNode *tree);  //前序二叉树遍历
    void InOrder(BSTNode *tree);  //中序二叉树遍历
    void PostOrder(BSTNode *tree);  //后序二叉树遍历
 
    BSTNode *search(BSTNode *x, int _key);  //递归实现，在”二叉树x“中查找_key节点
    BSTNode *IteratorSearch(BSTNode *x, int _key);  //迭代实现，在“二叉树x”中查找_key节点
 
    BSTNode *minimum(BSTNode *tree);  //查找最小节点：返回tree为根节点的二叉树的最小节点
    BSTNode *maximum(BSTNode *tree);  //查找最大节点：返回tree为根节点的二叉树的最大节点
 
    void insert(BSTNode *&tree, BSTNode *z);  // 将节点(z)插入到二叉树(tree)中
 
    BSTNode *remove(BSTNode *tree, BSTNode *z);  // 删除二叉树(tree)中的节点(z)，并返回被删除的节点
 
    void destroy(BSTNode *&tree);  //销毁二叉树
};

 
BinaryTree::BinaryTree() :_root(NULL) {}; 
 
BinaryTree::~BinaryTree() 
{
    destroy();
}
 
 
void BinaryTree::insert(int _key)  //将_key节点插入到二叉树中
{
    BSTNode *z = new BSTNode(_key, NULL, NULL, NULL);
    if (z == NULL)
    {
        return;  
    }
    insert(_root, z); 
}
 
 
void BinaryTree::PreOrder(BSTNode *tree)  //前序二叉树遍历
{
    if (tree != NULL)
    {
        cout << tree->_key << " ";
        PreOrder(tree->_left);
        PreOrder(tree->_right);
    }
}
void BinaryTree::PreOrder()
{
    PreOrder(_root); 
}
 
 
void BinaryTree::InOrder(BSTNode *tree)  //中序二叉树遍历
{
    if (tree != NULL)
    {
        InOrder(tree->_left);
        cout << tree->_key << " ";
        InOrder(tree->_right);
    }
}
void BinaryTree::InOrder()
{
    InOrder(_root);  
}
void BinaryTree::PostOrder(BSTNode *tree)  //后序二叉树遍历
{
    if (tree != NULL)
    {
        PostOrder(tree->_left);
        PostOrder(tree->_right);
        cout << tree->_key << " ";
    }
}
void BinaryTree::PostOrder()
{
    PostOrder(_root);  
}
BSTNode *BinaryTree::search(BSTNode *x, int _key)  //递归实现，在”二叉树x“中查找_key节点
{
    if (x == NULL || _key == x->_key)
    {
        return x;
    }
    if (_key < x->_key)
    {
        return search(x->_left, _key);
    }
    else
    {
        return search(x->_right, _key);
    }
}
BSTNode *BinaryTree::search(int _key)
{
    return search(_root, _key);  
}
BSTNode *BinaryTree::IteratorSearch(BSTNode *x, int _key)  //迭代实现，在“二叉树x”中查找_key节点
{
    while (x != NULL && _key != x->_key)
    {
        if (_key < x->_key)
        {
            x = x->_left;
        }
        else
        {
            x = x->_right;
        }
    }
    return x;
}
BSTNode *BinaryTree::IteratorSearch(int _key)
{
    return IteratorSearch(_root, _key);  //传入根节点和待查找的关键字_key
}
BSTNode *BinaryTree::minimum(BSTNode *tree)  //查找最小节点：返回tree为根节点的二叉树的最小节点。
{
    if (tree == NULL)
    {
        return NULL;
    }
    while (tree->_left != NULL)
    {
        tree = tree->_left;
    }
    return tree;
}

BSTNode *BinaryTree::maximum(BSTNode *tree)  //查找最大节点：返回tree为根节点的二叉树的最大节点。
{
    while (tree->_right != NULL)
    {
        tree = tree->_right;
    }
    return tree;
}
BSTNode *BinaryTree::successor(BSTNode *x)  //找节点(x)的后继节点，也就是该节点的右子树中的最小节点
{
    BSTNode *y = NULL;
    if (x->_right != NULL)
    {
        return minimum(x->_right);  
    }
    y  = x->_parent;
    while (y != NULL && x == y->_right)
    {
        x = y;
        y = y->_parent;
    }
    return y;
}
 
 
BSTNode *BinaryTree::predecessor(BSTNode *x)  //找节点(x)的前驱节点是该节点的左子树中的最大节点。
{
    BSTNode *y = NULL;
    if (x->_left != NULL)
    {
        return maximum(x->_left);
    }
    y = x->_parent;
    while (y != NULL && x == y->_left)
    {
        x = y;
        y = y->_parent;
    }
    return y;
}
 
 
void BinaryTree::insert(BSTNode *&tree, BSTNode *z)  // 将节点(z)插入到二叉树(tree)中
{
    BSTNode *y = NULL;
    BSTNode *x = tree;
 
    while (x != NULL) 
    {
        y = x;
        if (z->_key < x->_key)
        {
            x = x->_left;
        }
        else
        {
            x = x->_right;
        }
    }
 
    z->_parent = y;
    if (y == NULL)
    {
        tree = z;
    }
    else
        if (z->_key < y->_key)
        {
            y->_left = z;
        }
        else
        {
            y->_right = z;
        }
}
 
 
BSTNode *BinaryTree::remove(BSTNode *tree, BSTNode *z)  // 删除二叉树(tree)中的节点(z)，并返回被删除的节点
{
    BSTNode *x = NULL;
    BSTNode *y = NULL;
 
    if (z->_left == NULL || z->_right == NULL)
    {
        y = z;
    }
    else
    {
        y = successor(z);
    }
 
    if (y->_left != NULL)
    {
        x = y->_left;
    }
    else
    {
        x = y->_right;
    }
 
    if (x != NULL)
    {
        x->_parent = y->_parent;
    }
 
    if (y->_parent == NULL)
    {
        tree = x;
    }
    else
        if (y == y->_parent->_left)
        {
            y->_parent->_left = x;
        }
        else
        {
            y->_parent->_right = x;
        }
 
    if (y != z)
    {
        z->_key = y->_key;
    }
    return y;
}
 
 
void BinaryTree::remove(int _key)  // 删除二叉树(tree)中的节点(z)，并返回被删除的节点
{
    BSTNode *z, *node;
    z = IteratorSearch(_root, _key); 
    if (z == _root){
        cout<<"Root can't be delete!"<<endl;
    }
    if (z != NULL && z->_parent != NULL && z != _root)
    {
        node = remove(_root, z);  
        if (node != NULL)
        {
            delete node;
        }
    }
}
 
 
void BinaryTree::destroy(BSTNode *&tree)  //销毁二叉树
{
    if (tree == NULL)
    {
        return; 
    }
    if (tree->_left != NULL)
    {
        return destroy(tree->_left);
    }
    if (tree->_right != NULL)
    {
        return destroy(tree->_right);
    }
    delete tree;
    tree = NULL;
}
 
 
void BinaryTree::destroy()  //销毁二叉树
{
    destroy(_root);
}


int main()
{
    /************************/
    /*          插入
    /************************/
    BinaryTree *tree = new BinaryTree();
    int array[6] = {12, 33, 18, 24, 44, 66};
    cout << "二叉树数值：" << endl;
    for (int i = 0; i < 6; i++)
    {
        cout << array[i] << " ";
        tree->insert(array[i]);  //调用插入函数，生成二叉查找树
    }
 
    cout << endl << endl;
 
 
    /************************/
    /*          遍历           
    /************************/
    cout << "前序遍历：";
    tree->PreOrder();
    cout << endl;
 
    cout << "中序遍历：";
    tree->InOrder();
    cout << endl;
 
    cout << "后序遍历：";
    tree->PostOrder();
    cout << endl << endl;
 
 
    /************************/
    /*          查找           
    /************************/
    int _keyword;  //查找节点的关键字
    cout << "请输入要查找的节点：";
    cin >> _keyword;
    cout << endl;
    BSTNode *node = tree->IteratorSearch(_keyword);  //获取数值的地址
    if (node)  //判断有没有地址
    {
        cout << "关键字为“" << _keyword << "”的节点，存在。" << endl ;
    }
    else
    {
        cout << "关键字为“" << _keyword << "”的节点，不存在。" << endl;
    }
    cout << endl << endl;
 
 
    /************************/
    /*          删除
    /************************/
    int DelNode;  //要删除的节点
    cout << "请输入要删除的节点：";
    cin >> DelNode;
    tree->remove(DelNode);
    cout << endl;
 
    cout << "删除操作后，(前序)遍历：";
    tree->PreOrder();
    cout << endl;
    cout << "删除操作后，(中序)遍历：";
    tree->InOrder();
    cout << endl;
    cout << "删除操作后，(后序)遍历：";
    tree->PostOrder();
    cout << endl << endl;
    
 
    /************************/
    /*          销毁
    /************************/
    tree->destroy();
    system("pause");
    return 0;
}

```



