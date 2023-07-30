## Tree(트리)

트리는 **노드로 이루어진 자료 구조**

1. 트리는 하나의 루트 노드를 갖고 있다.
2. 루트 노드는 0개 이상의 자식 노드를 갖고 있다.
3. 그 자식 노드 또한 0개 이상의 자식 노드를 갖고 있고, 이는 반복적으로 정의된다.

- 노드(node)들과 노드들은 연결하는 간선(edge)들로 구성되어 있다.
  - 트리에는 사이클(cycle)이 존재 할 수 없다.
  - 노드들은 특정 순서로 나열될 수도 있고 그럴 수 없을 수도 잇다.
  - 각 노드는 부모 노드로의 연결이 있을 수도 있고 없을 수도 있다.
  - 각 노드는 어떤 자료형으로도 표현 가능하다.
- 트리는 비선형 자료구조로 계층적 관계를 표현한다. (디렉터리 구조, 조직도)
- 그래프의 한 종류
  - 사이클(cycle)이 없는 하나의 연결 그래프
  - 또는 DAG(Directed Acycli Graph, 방향성이 있는 비순환 그래프)의 한 종류

  ## 트리(Tree)와 관련된 용어
  ![트리](https://gmlwjd9405.github.io/images/data-structure-tree/tree-terms.png)
  
- 루트 노드(root node): 부모가 없는 노드, 트리는 하나의 루트 노드만을 가진다.  
- 단말 노드(leaf node): 자식이 없는 노드, '말단 노드' 또는 '잎 노드'라고도 부른다.
- 내부(internal) 노드: 단말 노드가 아닌 노드
- 간선(edge): 노드를 연결하는 선 (link, branch 라고도 부름)
- 형제(sibling): 같은 부모를 가지는 노드
- 노드의 크기(size): 자신을 포함한 모든 자손 노드의 개수
- 노드의 깊이(depth): 루트에서 어떤 노드에 도달하기 위해 거쳐야 하는 간선의 수
- 노드의 레벨(level): 트리의 특정 깊이를 가지는 노드의 집합
- 노드의 차수(degree): 하위 트리 개수 / 간선 수 (degree) = 각 노드가 지닌 가지의 수
- 트리의 차수(degree of tree): 트리의 최대 차수
- 트리의 높이(height): 루트 노드에서 가장 깊숙히 있는 노드의 깊이

## 트리(Tree)의 특징

-  그래프의 한 종류
-  계층 모델
-  사이클이 없다. 즉, 어떤 노드를 시작으로 자기 자신으로 돌아오는 경로가 없는 구조
-  단일 연결: 두 개의 노드를 잇는 간선은 단 하나만 존재

## 구현
```
// 이진 트리의 노드 클래스 정의
class TreeNode {
    int value;
    TreeNode left;
    TreeNode right;

    public TreeNode(int value) {
        this.value = value;
        this.left = null;
        this.right = null;
    }
}

// 이진 트리 클래스 정의
class BinaryTree {
    private TreeNode root;

    public BinaryTree() {
        root = null;
    }

    // 이진 트리에 노드 삽입
    public void insert(int value) {
        root = insertNode(root, value);
    }

    private TreeNode insertNode(TreeNode current, int value) {
        if (current == null) {
            return new TreeNode(value);
        }

        if (value < current.value) {
            current.left = insertNode(current.left, value);
        } else if (value > current.value) {
            current.right = insertNode(current.right, value);
        }

        return current;
    }

    // 이진 트리에서 노드 검색
    public boolean search(int value) {
        return searchNode(root, value);
    }

    private boolean searchNode(TreeNode current, int value) {
        if (current == null) {
            return false;
        }

        if (value == current.value) {
            return true;
        } else if (value < current.value) {
            return searchNode(current.left, value);
        } else {
            return searchNode(current.right, value);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        BinaryTree tree = new BinaryTree();

        // 이진 트리에 노드 삽입
        tree.insert(5);
        tree.insert(3);
        tree.insert(7);
        tree.insert(1);
        tree.insert(4);

        // 그림으로 보기
            5
           / \
          3   7
         / \
        1   4


        // 이진 트리에서 노드 검색
        System.out.println(tree.search(3)); // true
        System.out.println(tree.search(6)); // false
    }
}
```

## 응용 분야
- 게층적 데이터 구조: 파일 시스템, 조직도 등의 데이터를 표현하는데 사용
- 이진 검색 트리: 효율적인 데이터 검색을 위해 사용
- 힙(Heap) 자료구조: 우선순위 큐 등을 구현하는데 활용
- 트라이(Trie): 문자열 검색과 관련된 문제를 효울적으로 해결하는데 사용

Tree는 깊이 우선 탐색(DFS)과 너비 우선 탐색(BFS)과 같은 다양한 탐색 알고리즘을 적용하여 효율적으로 데이터를 탐색하고 처리할 수 있다.  
또한, Tree의 구조는 재귀적인 특성을 가지고 있기 때문에 재귀적인 알고리즘에도 자주 활용된다.  

