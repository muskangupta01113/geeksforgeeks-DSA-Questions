## 01. Count Pairs Violating BST Property

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/pairs-violating-bst-property--212515/1)

### Problem Description

**Task:** Given root of a binary tree in which all node values are distinct, count pairs of nodes that violate any of the following Binary Search Tree (BST) properties. All values in the left subtree are strictly smaller.All values in the right subtree are strictly greater.Examples:Input: root[] = [10, 50, 40, N, N, 20, 30]Output: 5

#### Examples

##### Example 1

- **Explanation:** There are total 10 pairs (80, 30), (80, 60), (80, 50), (30, 60), (40, 70), (40, 30), (40, 50), (70, 30), (70, 60), (70, 50) which violate the BST properties.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (3)

#### Solution 1 (C++)

- **Submitted:** 2026-10-23 22:21:05
- **Status:** Correct
- **Marks:** 0

```cpp
/* BST Node Structure
class Node {
public:
    int data;
    Node *left;
    Node *right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};
*/

class Solution {
  public:
    int pairsViolatingBST(Node* root) {
        vector<int> arr;

        function<void(Node*)> inorder = [&](Node* node) {
            if (!node) return;

            inorder(node->left);
            arr.push_back(node->data);
            inorder(node->right);
        };

        inorder(root);

        int ans = 0;

        function<void(int, int)> mergeSort = [&](int l, int r) {
            if (l >= r) return;

            int mid = l + (r - l) / 2;

            mergeSort(l, mid);
            mergeSort(mid + 1, r);

            vector<int> temp;
            int i = l, j = mid + 1;

            while (i <= mid && j <= r) {
                if (arr[i] <= arr[j]) {
                    temp.push_back(arr[i++]);
                } else {
                    ans += mid - i + 1;
                    temp.push_back(arr[j++]);
                }
            }

            while (i <= mid) temp.push_back(arr[i++]);
            while (j <= r) temp.push_back(arr[j++]);

            for (int k = l; k <= r; k++) {
                arr[k] = temp[k - l];
            }
        };

        mergeSort(0, (int)arr.size() - 1);
        return ans;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-10-23 21:43:25
- **Status:** Correct
- **Marks:** 0

```cpp
/* BST Node Structure
class Node {
public:
    int data;
    Node *left;
    Node *right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};
*/

class Solution {
  public:
    int pairsViolatingBST(Node* root) {
        vector<int> arr;

        function<void(Node*)> inorder = [&](Node* node) {
            if (!node) return;

            inorder(node->left);
            arr.push_back(node->data);
            inorder(node->right);
        };

        inorder(root);

        int ans = 0;

        function<void(int, int)> mergeSort = [&](int l, int r) {
            if (l >= r) return;

            int mid = l + (r - l) / 2;

            mergeSort(l, mid);
            mergeSort(mid + 1, r);

            vector<int> temp;
            int i = l, j = mid + 1;

            while (i <= mid && j <= r) {
                if (arr[i] <= arr[j]) {
                    temp.push_back(arr[i++]);
                } else {
                    ans += mid - i + 1;
                    temp.push_back(arr[j++]);
                }
            }

            while (i <= mid) temp.push_back(arr[i++]);
            while (j <= r) temp.push_back(arr[j++]);

            for (int k = l; k <= r; k++) {
                arr[k] = temp[k - l];
            }
        };

        mergeSort(0, (int)arr.size() - 1);
        return ans;
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2026-10-23 21:38:46
- **Status:** Correct
- **Marks:** 4

```cpp
/* BST Node Structure
class Node {
public:
    int data;
    Node *left;
    Node *right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};
*/

class Solution {
  public:
    int pairsViolatingBST(Node* root) {
        vector<int> arr;

        function<void(Node*)> inorder = [&](Node* node) {
            if (!node) return;

            inorder(node->left);
            arr.push_back(node->data);
            inorder(node->right);
        };

        inorder(root);

        int ans = 0;

        function<void(int, int)> mergeSort = [&](int l, int r) {
            if (l >= r) return;

            int mid = l + (r - l) / 2;

            mergeSort(l, mid);
            mergeSort(mid + 1, r);

            vector<int> temp;
            int i = l, j = mid + 1;

            while (i <= mid && j <= r) {
                if (arr[i] <= arr[j]) {
                    temp.push_back(arr[i++]);
                } else {
                    ans += mid - i + 1;
                    temp.push_back(arr[j++]);
                }
            }

            while (i <= mid) temp.push_back(arr[i++]);
            while (j <= r) temp.push_back(arr[j++]);

            for (int k = l; k <= r; k++) {
                arr[k] = temp[k - l];
            }
        };

        mergeSort(0, (int)arr.size() - 1);
        return ans;
    }
};
```

*Generated on: 10/23/2026, 10:29:19 PM*