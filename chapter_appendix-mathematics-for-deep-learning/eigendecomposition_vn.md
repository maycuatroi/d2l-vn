<!-- ===================== Bắt đầu dịch Phần 1 ==================== -->
<!-- ========================================= REVISE PHẦN 1 - BẮT ĐẦU =================================== -->

<!--
# Eigendecompositions
-->

# Phân tích trị riêng
:label:`sec_eigendecompositions`


<!--
Eigenvalues are often one of the most useful notions we will encounter when studying linear algebra, 
however, as a beginner, it is easy to overlook their importance.
Below, we introduce eigendecomposition and try to convey some sense of just why it is so important. 
-->

Trị riêng là một trong những khái niệm hữu ích nhất trong đại số tuyến tính,
tuy nhiên người mới học thường bỏ qua tầm quan trọng của chúng.
Dưới đây, chúng tôi giới thiệu phân tích trị riêng (*eigendecomposition*) và cố gắng truyền tải tầm quan trọng của chúng.


<!--
Suppose that we have a matrix $A$ with the following entries:
-->

Giả sử ta có một ma trận $A$ với các đầu vào sau:


$$
\mathbf{A} = \begin{bmatrix}
2 & 0 \\
0 & -1
\end{bmatrix}.
$$


<!--
If we apply $A$ to any vector $\mathbf{v} = [x, y]^\top$, we obtain a vector $\mathbf{A}\mathbf{v} = [2x, -y]^\top$.
This has an intuitive interpretation: stretch the vector to be twice as wide in the $x$-direction, and then flip it in the $y$-direction.
-->

Nếu ta áp dụng $A$ cho bất kỳ vector $\mathbf{v} = [x, y]^\top$ nào, ta nhận được một vector $\mathbf{A}\mathbf{v} = [2x, -y]^\top$.
Có thể diễn giải theo trực giác như sau: kéo vector dài gấp đôi theo hướng $x$, rồi đảo ngược theo hướng $y$.


<!--
However, there are *some* vectors for which something remains unchanged.
Namely $[1, 0]^\top$ gets sent to $[2, 0]^\top$ and $[0, 1]^\top$ gets sent to $[0, -1]^\top$.
These vectors are still in the same line, and the only modification is that the matrix stretches them by a factor of $2$ and $-1$ respectively.
We call such vectors *eigenvectors* and the factor they are stretched by *eigenvalues*.
-->

Tuy nhiên, có *một vài* vector mà với chúng có một số thứ không thay đổi.
Ví dụ như $[1, 0]^\top$ được biến đổi thành $[2, 0]^\top$ và $[0, 1]^\top$ được biến đổi thành $[0, -1]^\top$.
Những vector này không thay đổi phương, chỉ bị kéo giãn theo tỷ lệ với hệ số $2$ và $-1$.
Ta gọi những vector ấy là *vector riêng* và các hệ số làm chúng giãn ra gọi là *trị riêng*.


<!--
In general, if we can find a number $\lambda$ and a vector $\mathbf{v}$ such that 
-->

Tổng quát, nếu ta tìm được một số $\lambda$ và một vector $\mathbf{v}$ mà 


$$
\mathbf{A}\mathbf{v} = \lambda \mathbf{v}.
$$


<!--
We say that $\mathbf{v}$ is an eigenvector for $A$ and $\lambda$ is an eigenvalue.
-->

Ta nói rằng $\mathbf{v}$ là một vector riêng và $\lambda$ là một trị riêng của $A$.


<!--
## Finding Eigenvalues
-->

## Tìm trị riêng


<!--
Let us figure out how to find them. By subtracting off the $\lambda \mathbf{v}$ from both sides, and then factoring out the vector, we see the above is equivalent to:
-->

Ta hãy tìm hiểu cách tìm trị riêng. Bằng cách trừ đi $\lambda \mathbf{v}$ ở cả hai vế, rồi sau đó nhóm thừa số chung là vector, ta thấy phần phía trên tương đương với:


$$(\mathbf{A} - \lambda \mathbf{I})\mathbf{v} = 0.$$
:eqlabel:`eq_eigvalue_der`


<!--
For :eqref:`eq_eigvalue_der` to happen, we see that $(\mathbf{A} - \lambda \mathbf{I})$ must compress some direction down to zero, hence it is not invertible, and thus the determinant is zero.
Thus, we can find the *eigenvalues* by finding for what $\lambda$ is $\det(\mathbf{A}-\lambda \mathbf{I}) = 0$.
Once we find the eigenvalues, we can solve $\mathbf{A}\mathbf{v} = \lambda \mathbf{v}$ to find the associated *eigenvector(s)*.
-->

Để :eqref:`eq_eigvalue_der` xảy ra, ta thấy rằng $(\mathbf{A} - \lambda \mathbf{I})$ phải nén một số chiều xuống không, vì thế nó không thể nghịch đảo, nên định thức vì thế bằng không.
Vì thế, ta có thể tìm các *trị riêng* bằng cách giải phương trình $\lambda$ is $\det(\mathbf{A}-\lambda \mathbf{I}) = 0$.
Một khi ta tìm được các trị riêng, ta có thể giải bài toán $\mathbf{A}\mathbf{v} = \lambda \mathbf{v}$ để tìm (các) *vector riêng* tương ứng.

<!-- ===================== Kết thúc dịch Phần 1 ===================== -->

<!-- ===================== Bắt đầu dịch Phần 2 ===================== -->

<!--
### An Example
-->

### Ví dụ


<!--
Let us see this with a more challenging matrix
-->

Hãy xét một ma trận thách thức hơn


$$
\mathbf{A} = \begin{bmatrix}
2 & 1\\
2 & 3 
\end{bmatrix}.
$$


<!--
If we consider $\det(\mathbf{A}-\lambda \mathbf{I}) = 0$, we see this is equivalent to the polynomial equation $0 = (2-\lambda)(3-\lambda)-2 = (4-\lambda)(1-\lambda)$.
Thus, two eigenvalues are $4$ and $1$.
To find the associated vectors, we then need to solve
-->

Nếu ta để ý $\det(\mathbf{A}-\lambda \mathbf{I}) = 0$, ta thấy rằng điều này tương đương với phương trình đa thức $0 = (2-\lambda)(3-\lambda)-2 = (4-\lambda)(1-\lambda)$.
Như vậy, hai trị riêng đó là $4$ và $1$.
Để tìm các vector tương đương, ta cần phải giải hệ phương trình 


$$
\begin{bmatrix}
2 & 1\\
2 & 3 
\end{bmatrix}\begin{bmatrix}x \\ y\end{bmatrix} = \begin{bmatrix}x \\ y\end{bmatrix}  \; \text{and} \;
\begin{bmatrix}
2 & 1\\
2 & 3 
\end{bmatrix}\begin{bmatrix}x \\ y\end{bmatrix}  = \begin{bmatrix}4x \\ 4y\end{bmatrix} .
$$


<!--
We can solve this with the vectors $[1, -1]^\top$ and $[1, 2]^\top$ respectively.
-->

Ta có thể giải bài toán lần lượt với các vector $[1, -1]^\top$ và $[1, 2]^\top$.


<!--
We can check this in code using the built-in `numpy.linalg.eig` routine.
-->

Ta có thể kiểm tra điều này bằng đoạn mã sử dụng trong chương trình con có sẵn `numpy.linalg.eig`.


```{.python .input}
%matplotlib inline
from d2l import mxnet as d2l
from IPython import display
import numpy as np

np.linalg.eig(np.array([[2, 1], [2, 3]]))
```

```{.python .input}
#@tab pytorch
%matplotlib inline
from d2l import torch as d2l
from IPython import display
import torch

torch.eig(torch.tensor([[2, 1], [2, 3]], dtype=torch.float64),
          eigenvectors=True)
```

```{.python .input}
#@tab tensorflow
%matplotlib inline
from d2l import tensorflow as d2l
from IPython import display
import tensorflow as tf

tf.linalg.eigh(tf.constant([[2, 1], [2, 3]], dtype=tf.float64))
```


<!--
Note that `numpy` normalizes the eigenvectors to be of length one, whereas we took ours to be of arbitrary length.
Additionally, the choice of sign is arbitrary.
However, the vectors computed are parallel to the ones we found by hand with the same eigenvalues.
-->

Lưu ý rằng `numpy` chuẩn hóa các vector riêng trở về độ dài bằng một, trong khi các vector của chúng tôi có độ dài tùy ý.
Thêm vào đó, việc chọn dấu cũng là tùy ý.
Tuy nhiên, các vector được tính toán thì song song với các vector chúng ta đã tìm ra theo cách thủ công khi sử dụng cùng trị riêng. 


<!--
## Decomposing Matrices
-->

## Phân rã Ma trận


<!--
Let us continue the previous example one step further.  Let
-->

Hãy tiếp tục với ví dụ trước đó bằng cách tiến xa hơn một bước. Cho


$$
\mathbf{W} = \begin{bmatrix}
1 & 1 \\
-1 & 2
\end{bmatrix},
$$


<!--
be the matrix where the columns are the eigenvectors of the matrix $\mathbf{A}$. Let
-->

là ma trận có các cột là vector riêng của ma trận $\mathbf{A}$. Cho


$$
\boldsymbol{\Sigma} = \begin{bmatrix}
1 & 0 \\
0 & 4
\end{bmatrix},
$$


<!--
be the matrix with the associated eigenvalues on the diagonal.
Then the definition of eigenvalues and eigenvectors tells us that
-->

là ma trận với các trị riêng tương ứng nằm trên đường chéo.
Rồi từ định nghĩa của trị riêng và vector riêng, ta có

$$
\mathbf{A}\mathbf{W} =\mathbf{W} \boldsymbol{\Sigma} .
$$


<!--
The matrix $W$ is invertible, so we may multiply both sides by $W^{-1}$ on the right, we see that we may write
-->

Ma trận $W$ là khả nghịch, nên ta có thể nhân hai vế với $W^{-1}$ phía bên phải, để có


$$\mathbf{A} = \mathbf{W} \boldsymbol{\Sigma} \mathbf{W}^{-1}.$$
:eqlabel:`eq_eig_decomp`


<!--
In the next section we will see some nice consequences of this, but for now we need only know that such a decomposition 
will exist as long as we can find a full collection of linearly independent eigenvectors (so that $W$ is invertible).
-->

Trong phần tiếp theo ta sẽ thấy một số hệ quả hay ho từ diều này, nhưng bây giờ ta chỉ cần biết rằng phân rã như vậy 
sẽ tồn tại nếu ta có thể tìm tất cả các vector riêng độc lập tuyến tính (để ma trận $W$ khả nghịch). 

<!-- ===================== Kết thúc dịch Phần 2 ===================== -->

<!-- ===================== Bắt đầu dịch Phần 3 ===================== -->

<!--
## Operations on Eigendecompositions
-->

## Các phép toán dùng phân tích trị riêng


<!--
One nice thing about eigendecompositions :eqref:`eq_eig_decomp` is that we can write many operations we usually encounter cleanly 
in terms of the eigendecomposition. As a first example, consider:
-->

Một điều hay về phân tích trị riêng :eqref:`eq_eig_decomp` là ta có thể viết nhiều phép toán thường gặp một cách gọn gàng
về mặt phân tích trị riêng. Ví dụ đầu tiên, xem xét:


$$
\mathbf{A}^n = \overbrace{\mathbf{A}\cdots \mathbf{A}}^{\text{$n$ times}} = \overbrace{(\mathbf{W}\boldsymbol{\Sigma} \mathbf{W}^{-1})\cdots(\mathbf{W}\boldsymbol{\Sigma} \mathbf{W}^{-1})}^{\text{$n$ times}} =  \mathbf{W}\overbrace{\boldsymbol{\Sigma}\cdots\boldsymbol{\Sigma}}^{\text{$n$ times}}\mathbf{W}^{-1} = \mathbf{W}\boldsymbol{\Sigma}^n \mathbf{W}^{-1}.
$$


<!--
This tells us that for any positive power of a matrix, the eigendecomposition is obtained by just raising the eigenvalues to the same power.
The same can be shown for negative powers, so if we want to invert a matrix we need only consider
-->

Điều này cho chúng ta biết rằng với bất kỳ số mũ dương nào của một ma trận, phân tích trị riêng đạt được bằng cách lũy thừa các trị riêng lên cùng số mũ.
Điều tương tự cũng có thể được chứng minh cho các số mũ âm, vì nếu ta muốn nghịch đảo một ma trận ta chỉ cần xét


$$
\mathbf{A}^{-1} = \mathbf{W}\boldsymbol{\Sigma}^{-1} \mathbf{W}^{-1},
$$


<!--
or in other words, just invert each eigenvalue.
This will work as long as each eigenvalue is non-zero, so we see that invertible is the same as having no zero eigenvalues.  
-->

hay nói cách khác, chỉ cần nghịch đảo từng trị riêng một.
Điều này có thể thực hiện chỉ cần các trị riêng khác không, vì thế khả nghịch tương đương với không có trị riêng bằng không.


<!--
Indeed, additional work can show that if $\lambda_1, \ldots, \lambda_n$ are the eigenvalues of a matrix, then the determinant of that matrix is
-->

Thật sự, có thể chứng minh rằng nếu $\lambda_1, \ldots, \lambda_n$ là các trị riêng của một ma trận, định thức của ma trận đó sẽ là 


$$
\det(\mathbf{A}) = \lambda_1 \cdots \lambda_n,
$$


<!--
or the product of all the eigenvalues.
This makes sense intuitively because whatever stretching $\mathbf{W}$ does, $W^{-1}$ undoes it, so in the end the only stretching that happens is 
by multiplication by the diagonal matrix $\boldsymbol{\Sigma}$, which stretches volumes by the product of the diagonal elements.
-->

hay là tích của tất cả các trị riêng.
Điều này hợp lý theo trực giác vì nếu kéo giãn ma trận $\mathbf{W}$ thế nào, thì $W^{-1}$ sẽ hoàn tác nó, vì thế cuối cùng kéo giãn duy nhất là việc nhân với ma trận đường chéo $\boldsymbol{\Sigma}$, sẽ kéo giãn độ lớn bằng tích của các phần tử trên đường chéo.


<!--
Finally, recall that the rank was the maximum number of linearly independent columns of your matrix.
By examining the eigendecomposition closely, we can see that the rank is the same as the number of non-zero eigenvalues of $\mathbf{A}$.
-->

Cuối cùng, ta hãy nhớ lại rằng hạng ma trận là số lượng cột độc lập tuyến tính lớn nhất của ma trận.
Bằng cách kiểm nghiệm phân tích trị riêng một cách chặt chẽ, ta có thể thấy rằng hạng bằng số lượng các trị riêng khác không của $\mathbf{A}$.


<!--
The examples could continue, but hopefully the point is clear: eigendecomposition can simplify many linear-algebraic computations
and is a fundamental operation underlying many numerical algorithms and much of the analysis that we do in linear algebra. 
-->

Trước khi tiếp tục, hy vọng bạn đọc hiểu được luận điểm: phân tích trị riêng có thể đơn giản hóa nhiều phép tính đại số tuyến tính
và là một phép toán cơ bản phía sau nhiều thuật toán số và nhiều phân tích mà ta thực hiện trong đại số tuyến tính. 

<!-- ===================== Kết thúc dịch Phần 3 ===================== -->

<!-- ===================== Bắt đầu dịch Phần 4 ===================== -->

<!--
## Eigendecompositions of Symmetric Matrices
-->

## Phân tích trị riêng của ma trận đối xứng


<!--
It is not always possible to find enough linearly independent eigenvectors for the above process to work. For instance the matrix
-->

Không phải lúc nào ta cũng có thể tìm đủ các vector riêng độc lập tuyến tính để quy trình phía trên hoạt động. Ví dụ ma trận sau


$$
\mathbf{A} = \begin{bmatrix}
1 & 1 \\
0 & 1
\end{bmatrix},
$$


<!--
has only a single eigenvector, namely $(1, 0)^\top$. 
To handle such matrices, we require more advanced techniques than we can cover (such as the Jordan Normal Form, or Singular Value Decomposition).
We will often need to restrict our attention to those matrices where we can guarantee the existence of a full set of eigenvectors.
-->

chỉ có duy nhất một vector riêng, gọi là $(1, 0)^\top$. 
Để xử lý những ma trận như thế, ta cần những kỹ thuật cao cấp hơn những gì đã đề cập (ví dụ như dạng chuẩn Jordan, hay phân tích đơn trị). 
Ta thường sẽ cần hạn chế chú ý đến những ma trận mà ta có thể đảm bảo tồn tại một bộ đầy đủ các vector riêng. 

<!--
The most commonly encountered family are the *symmetric matrices*, which are those matrices where $\mathbf{A} = \mathbf{A}^\top$. 
In this case, we may take $W$ to be an *orthogonal matrix*—a matrix whose columns are all length one vectors that are at right angles to one another,
where $\mathbf{W}^\top = \mathbf{W}^{-1}$—and all the eigenvalues will be real.  
Thus, in this special case, we can write :eqref:`eq_eig_decomp` as
-->

Họ vector thường gặp nhất là *ma trận đối xứng*, là những ma trận mà $\mathbf{A} = \mathbf{A}^\top$. 
Trong trường hợp này, ta có thể lấy $W$ trở thành *ma trận trực giao* - ma trận mà các cột của nó là các vector có độ dài bằng một và vuông góc với nhau,
tại $\mathbf{W}^\top = \mathbf{W}^{-1}$ - và tất cả các trị riêng sẽ là số thực.
Do đó, trong trường hợp đặc biệt này, ta có thể viết :eqref:`eq_eig_decomp` như là


$$
\mathbf{A} = \mathbf{W}\boldsymbol{\Sigma}\mathbf{W}^\top .
$$


<!--
## Gershgorin Circle Theorem
-->

## Định lý vòng tròn Gershgorin


<!--
Eigenvalues are often difficult to reason with intuitively.
If presented an arbitrary matrix, there is little that can be said about what the eigenvalues are without computing them.
There is, however, one theorem that can make it easy to approximate well if the largest values are on the diagonal.
-->

Các trị riêng thường khó để tư duy bằng trực giác.
Nếu tồn tại một ma trận bất kỳ, ta chỉ có thể nói rất ít về trị riêng nếu không tính toán chúng.
Tuy nhiên, tồn tại một định lý giúp dễ dàng xấp xỉ tốt trị riêng nếu các giá trị lớn nhất của ma trận nằm trên đường chéo. 

<!--
Let $\mathbf{A} = (a_{ij})$ be any square matrix ($n\times n$).
We will define $r_i = \sum_{j \neq i} |a_{ij}|$.
Let $\mathcal{D}_i$ represent the disc in the complex plane with center $a_{ii}$ radius $r_i$.
Then, every eigenvalue of $\mathbf{A}$ is contained in one of the $\mathcal{D}_i$.
-->

Cho $\mathbf{A} = (a_{ij})$ là ma trận vuông bất kỳ ($n\times n$).
Ta sẽ định nghĩa $r_i = \sum_{j \neq i} |a_{ij}|$.
Cho $\mathcal{D}_i$ biểu diễn hình tròn trong mặt phẳng phức với tâm là $a_{ii}$, bán kính $r_i$.
Kế đó, mỗi trị riêng của $\mathbf{A}$ được chứa ở một trong các $\mathcal{D}_i$.


<!--
This can be a bit to unpack, so let us look at an example.  
Consider the matrix:
-->

Điều này có thể hơi khó hiểu một chút, nên ta hãy nhìn vào ví dụ sau.
Xem xét ma trận:


$$
\mathbf{A} = \begin{bmatrix}
1.0 & 0.1 & 0.1 & 0.1 \\
0.1 & 3.0 & 0.2 & 0.3 \\
0.1 & 0.2 & 5.0 & 0.5 \\
0.1 & 0.3 & 0.5 & 9.0
\end{bmatrix}.
$$


<!--
We have $r_1 = 0.3$, $r_2 = 0.6$, $r_3 = 0.8$ and $r_4 = 0.9$.
The matrix is symmetric, so all eigenvalues are real.
This means that all of our eigenvalues will be in one of the ranges of 
-->

Ta có $r_1 = 0.3$, $r_2 = 0.6$, $r_3 = 0.8$ và $r_4 = 0.9$.
Ma trận này đối xứng, tất cả các trị riêng đều là số thực.
Điều này có nghĩa tất cả các trị riêng sẽ là một trong các khoảng của 


$$[a_{11}-r_1, a_{11}+r_1] = [0.7, 1.3], $$

$$[a_{22}-r_2, a_{22}+r_2] = [2.4, 3.6], $$

$$[a_{33}-r_3, a_{33}+r_3] = [4.2, 5.8], $$

$$[a_{44}-r_4, a_{44}+r_4] = [8.1, 9.9]. $$


<!--
Performing the numerical computation shows 
that the eigenvalues are approximately $0.99$, $2.97$, $4.95$, $9.08$,
all comfortably inside the ranges provided.
-->

Thực hiện việc tính toán số cho thấy
rằng các trị riêng xấp xỉ ở $0.99$, $2.97$, $4.95$, $9.08$,
đều nằm trong các khoảng cho trước một cách thoải mái.


```{.python .input}
A = np.array([[1.0, 0.1, 0.1, 0.1],
              [0.1, 3.0, 0.2, 0.3],
              [0.1, 0.2, 5.0, 0.5],
              [0.1, 0.3, 0.5, 9.0]])

v, _ = np.linalg.eig(A)
v
```

```{.python .input}
#@tab pytorch
A = torch.tensor([[1.0, 0.1, 0.1, 0.1],
              [0.1, 3.0, 0.2, 0.3],
              [0.1, 0.2, 5.0, 0.5],
              [0.1, 0.3, 0.5, 9.0]])

v, _ = torch.eig(A)
v
```

```{.python .input}
#@tab tensorflow
A = tf.constant([[1.0, 0.1, 0.1, 0.1],
                [0.1, 3.0, 0.2, 0.3],
                [0.1, 0.2, 5.0, 0.5],
                [0.1, 0.3, 0.5, 9.0]])

v, _ = tf.linalg.eigh(A)
v
```


<!--
In this way, eigenvalues can be approximated, and the approximations will be fairly accurate 
in the case that the diagonal is significantly larger than all the other elements.  
-->

Bằng cách này, các trị riêng có thể được tính xấp xỉ khá chính xác
trong trường hợp đường chéo lớn hơn hẳn so với các phần tử còn lại.


<!--
It is a small thing, but with a complex and subtle topic like eigendecomposition, 
it is good to get any intuitive grasp we can.
-->

Điều này tuy nhỏ nhưng với một chủ đề phức tạp và tinh vi như phân tích trị riêng,
thật tốt nếu có thể hiểu bất kỳ trực quan nào.

<!-- ===================== Kết thúc dịch Phần 4 ===================== -->

<!-- ===================== Bắt đầu dịch Phần 5 ===================== -->

<!--
## A Useful Application: The Growth of Iterated Maps
-->

## *dịch tiêu đề trên*


<!--
Now that we understand what eigenvectors are in principle, let us see how they can be used to provide a deep understanding 
of a problem central to neural network behavior: proper weight initialization. 
-->

*dịch đoạn phía trên*


<!--
### Eigenvectors as Long Term Behavior
-->

### *dịch tiêu đề trên*


<!--
The full mathematical investigation of the initialization of deep neural networks is beyond the scope of the text, 
but we can see a toy version here to understand how eigenvalues can help us see how these models work.
As we know, neural networks operate by interspersing layers of linear transformations with non-linear operations.
For simplicity here, we will assume that there is no non-linearity,
and that the transformation is a single repeated matrix operation $A$,so that the output of our model is
-->

*dịch đoạn phía trên*


$$
\mathbf{v}_{out} = \mathbf{A}\cdot \mathbf{A}\cdots \mathbf{A} \mathbf{v}_{in} = \mathbf{A}^N \mathbf{v}_{in}.
$$


<!--
When these models are initialized, $A$ is taken to be a random matrix with Gaussian entries, so let us make one of those. 
To be concrete, we start with a mean zero, variance one Gaussian distributed $5 \times 5$ matrix.
-->

*dịch đoạn phía trên*


```{.python .input}
np.random.seed(8675309)

k = 5
A = np.random.randn(k, k)
A
```

```{.python .input}
#@tab pytorch
torch.manual_seed(42)

k = 5
A = torch.randn(k, k, dtype=torch.float64)
A
```

```{.python .input}
#@tab tensorflow
k = 5
A = tf.random.normal((k, k), dtype=tf.float64)
A
```

<!-- ========================================= REVISE PHẦN 1 - KẾT THÚC ===================================-->

<!-- ========================================= REVISE PHẦN 2 - BẮT ĐẦU ===================================-->

<!--
### Behavior on Random Data
-->

### Hành vi trên Dữ liệu Ngẫu nhiên


<!--
For simplicity in our toy model, we will assume that the data vector we feed in $\mathbf{v}_{in}$ is a random five dimensional Gaussian vector.
Let us think about what we want to have happen.
For context, lets think of a generic ML problem, where we are trying to turn input data, like an image, into a prediction, like the probability the image is a picture of a cat.
If repeated application of $\mathbf{A}$ stretches a random vector out to be very long, 
then small changes in input will be amplified into large changes in output---tiny modifications of the input image would lead to vastly different predictions.
This does not seem right!
-->

Ttrong mô hình đơn giản, ta giả sử rằng vector dữ liệu ta đưa vào trong $\mathbf{v}_{in}$ là một vector Gauss ngẫu nhiên năm chiều.
Hãy thử nghĩ xem ta sẽ muốn cái gì xảy ra.
Trong ngữ cảnh này, hãy liên tưởng tới một bài toán ML nói chung, trong đó ta đang cố biến dữ liệu đầu vào, như một ảnh, thành một dự đoán, như xác suất ảnh đó là bức ảnh một con mèo.
Nếu phép khai triển liên tục của $\mathbf{A}$ khiến một vector ngẫu liên bị kéo dãn lên quá dài
thì chỉ với một thay đổi nhỏ trên đầu vào cũng có thể khuếch đại thành một thay đổi lớn trên đầu ra -- các sự biến đổi nhỏ trên ảnh đầu vào cũng có thể dẫn tới các dự đoán vô cùng khác.
Việc này dường như không hợp lý!


<!--
On the flip side, if $\mathbf{A}$ shrinks random vectors to be shorter,
then after running through many layers, the vector will essentially shrink to nothing, 
and the output will not depend on the input. This is also clearly not right either!
-->

Trái lại, nếu $\mathbf{A}$ khiến các vector ngẫu nhiên co ngắn lại,
thì sau khi đi qua nhiều tầng, vector này về cơ bản sẽ co đến mức chẳng còn lại gì,
và đầu ra sẽ không còn phụ thuộc vào đầu vào. Rõ ràng là việc này cũng không hề hợp lý!


<!--
We need to walk the narrow line between growth and decay 
to make sure that our output changes depending on our input, but not much!
-->

Ta cần tìm ra ranh giới giữa tăng trưởng và suy giảm
để đảm bảo rằng thay đổi trên đầu ra phụ thuộc vào đầu vào của ta, nhưng không quá phụ thuộc!


<!--
Let us see what happens when we repeatedly multiply our matrix $\mathbf{A}$ 
against a random input vector, and keep track of the norm.
-->

Hãy xem chuyện gì sẽ xảy ra nếu ta liên tục nhân ma trận $\mathbf{A}$
với một vector đầu vào ngẫu nhiên, và theo dõi giá trị chuẩn (*norm*).


```{.python .input}
# Calculate the sequence of norms after repeatedly applying `A`
v_in = np.random.randn(k, 1)

norm_list = [np.linalg.norm(v_in)]
for i in range(1, 100):
    v_in = A.dot(v_in)
    norm_list.append(np.linalg.norm(v_in))

d2l.plot(np.arange(0, 100), norm_list, 'Iteration', 'Value')
```

```{.python .input}
#@tab pytorch
# Calculate the sequence of norms after repeatedly applying `A`
v_in = torch.randn(k, 1, dtype=torch.float64)

norm_list = [torch.norm(v_in).item()]
for i in range(1, 100):
    v_in = A @ v_in
    norm_list.append(torch.norm(v_in).item())

d2l.plot(torch.arange(0, 100), norm_list, 'Iteration', 'Value')
```

```{.python .input}
#@tab tensorflow
# Calculate the sequence of norms after repeatedly applying `A`
v_in = tf.random.normal((k, 1), dtype=tf.float64)

norm_list = [tf.norm(v_in).numpy()]
for i in range(1, 100):
    v_in = tf.matmul(A, v_in)
    norm_list.append(tf.norm(v_in).numpy())

d2l.plot(tf.range(0, 100), norm_list, 'Iteration', 'Value')
```


<!--
The norm is growing uncontrollably! 
Indeed if we take the list of quotients, we will see a pattern.
-->

Giá trị chuẩn tăng một cách không thể kiểm soát được!
Quả thực, nếu ta lấy ra danh sách các tỉ số, ta sẽ thấy một khuôn mẫu.


```{.python .input}
# Compute the scaling factor of the norms
norm_ratio_list = []
for i in range(1, 100):
    norm_ratio_list.append(norm_list[i]/norm_list[i - 1])

d2l.plot(np.arange(1, 100), norm_ratio_list, 'Iteration', 'Ratio')
```

```{.python .input}
#@tab pytorch
# Compute the scaling factor of the norms
norm_ratio_list = []
for i in range(1, 100):
    norm_ratio_list.append(norm_list[i]/norm_list[i - 1])

d2l.plot(torch.arange(1, 100), norm_ratio_list, 'Iteration', 'Ratio')
```

```{.python .input}
#@tab tensorflow
# Compute the scaling factor of the norms
norm_ratio_list = []
for i in range(1, 100):
    norm_ratio_list.append(norm_list[i]/norm_list[i - 1])

d2l.plot(tf.range(1, 100), norm_ratio_list, 'Iteration', 'Ratio')
```


<!--
If we look at the last portion of the above computation, 
we see that the random vector is stretched by a factor of `1.974459321485[...]`,
where the portion at the end shifts a little, 
but the stretching factor is stable.  
-->

Nếu quan sát phần cuối của phép tính trên,
ta có thể thấy rằng vector ngẫu nhiên bị kéo dãn `1.974459321485[...]` lần,
với phần số thập phân ở cuối có thay đổi một chút,
nhưng hệ số dãn đã ổn định.

<!-- ===================== Kết thúc dịch Phần 5 ===================== -->

<!-- ===================== Bắt đầu dịch Phần 6 ===================== -->

<!--
### Relating Back to Eigenvectors
-->

### Liên hệ Ngược lại tới Vector riêng


<!--
We have seen that eigenvectors and eigenvalues correspond to the amount something is stretched, 
but that was for specific vectors, and specific stretches.
Let us take a look at what they are for $\mathbf{A}$.
A bit of a caveat here: it turns out that to see them all, we will need to go to complex numbers.
You can think of these as stretches and rotations.
By taking the norm of the complex number (square root of the sums of squares of real and imaginary parts)
we can measure that stretching factor. Let us also sort them.
-->

Ta đã thấy rằng vector riêng và trị riêng tương ứng với mức độ co dãn của thứ gì đó,
nhưng đó là với các vector cụ thể, và các phép co dãn cụ thể.
Hãy cùng xét xem đó là gì đối với $\mathbf{A}$.
Nói trước một chút: hoá ra là để có thể quan sát toàn bộ các mức độ đó, ta cần xét tới số phức.
Bạn có thể coi chúng như phép co dãn và phép quay.
Bằng cách tính mô-đun của số phức (căn bậc hai của tổng bình phương phần thực và phần ảo),
ta có thể đo hệ số co dãn. Ta cũng cần phải sắp xếp chúng.


```{.python .input}
# Compute the eigenvalues
eigs = np.linalg.eigvals(A).tolist()
norm_eigs = [np.absolute(x) for x in eigs]
norm_eigs.sort()
print(f'norms of eigenvalues: {norm_eigs}')
```

```{.python .input}
#@tab pytorch
# Compute the eigenvalues
eigs = torch.eig(A)[0][:,0].tolist()
norm_eigs = [torch.abs(torch.tensor(x)) for x in eigs]
norm_eigs.sort()
print(f'norms of eigenvalues: {norm_eigs}')
```

```{.python .input}
#@tab tensorflow
# Compute the eigenvalues
eigs = tf.linalg.eigh(A)[0].numpy().tolist()
norm_eigs = [tf.abs(tf.constant(x, dtype=tf.float64)) for x in eigs]
norm_eigs.sort()
print(f'norms of eigenvalues: {norm_eigs}')
```


<!--
### An Observation
-->

### Nhận xét


<!--
We see something a bit unexpected happening here: that number we identified before for the long term stretching of our matrix $\mathbf{A}$ 
applied to a random vector is *exactly* (accurate to thirteen decimal places!) the largest eigenvalue of $\mathbf{A}$.
This is clearly not a coincidence!
-->

Ta quan sát thấy một chút bất thường ở đây: rằng số mà ta xác định từ trước cho quá trình dãn liên tục trên ma trận $\mathbf{A}$
khai triển lên một vector ngẫu nhiên lại *chính là* trị riêng lớn nhất của $\mathbf{A}$ (chính xác đến 13 số thập phân).
Điều này rõ ràng không phải một sự trùng hợp.


<!--
But, if we now think about what is happening geometrically, this starts to make sense. Consider a random vector. 
This random vector points a little in every direction, so in particular, it points at least a little bit 
in the same direction as the eigenvector of $\mathbf{A}$ associated with the largest eigenvalue.
This is so important that it is called the *principle eigenvalue* and *principle eigenvector*.
After applying $\mathbf{A}$, our random vector gets stretched in every possible direction,
as is associated with every possible eigenvector, but it is stretched most of all in the direction associated with this principle eigenvector.
What this means is that after apply in $A$, our random vector is longer, and points in a direction closer to being aligned with the principle eigenvector.
After applying the matrix many times, the alignment with the principle eigenvector becomes closer and closer until, 
for all practical purposes, our random vector has been transformed into the principle eigenvector!
Indeed this algorithm is the basis for what is known as the *power iteration* for finding the largest eigenvalue and eigenvector of a matrix.
For details see, for example, :cite:`Van-Loan.Golub.1983`.
-->

Tuy nhiên, nếu ta thực sự suy ngẫm chuyện gì đang xảy ra trên phương diện hình học, điều này bắt đầu hợp lý. Xét một vector ngẫu nhiên.
Vector ngẫu nhiên này trỏ tới mỗi hướng một chút, nên cụ thể, nó chút ít cũng trỏ tới
cùng hướng với vector riêng của $\mathbf{A}$ tương ứng với trị riêng lớn nhất.
Trị riêng này quan trọng đến mức nó được gọi là *trị riêng chính (principle eigenvalue)* và *vector riêng chính (principle eigenvector)*.
Sau khi khai triển $\mathbf{A}$, vector ngẫu nhiên trên bị dãn ra theo mọi hướng có thể,
do nó liên kết với mọi vector riêng có thể, nhưng nó bị dãn nhiều nhất trên hướng liên kết với vector riêng chính.
Điều này có nghĩa là sau khi khai triển trên $A$, vector ngẫu nhiên trên dài ra, và ngày càng cùng hướng với vector riêng chính.
Sau khi áp dụng ma trận nhiều lần, vector ngẫu nhiên ngày càng gần vector riêng chính cho tới khi,
nhằm mọi mục định thực tế, vector này trở thành vector riêng chính.
Đây là cơ sở cho thuật toán *lặp lũy thừa - (power iteration)* để tìm trị riêng và vector riêng lớn nhất của một ma trận.
Chi tiết có thể tham khảo tại :cite:`Van-Loan.Golub.1983`.


<!--
### Fixing the Normalization
-->

### Khắc phục với Chuẩn hoá


<!--
Now, from above discussions, we concluded that we do not want a random vector to be stretched or squished at all,
we would like random vectors to stay about the same size throughout the entire process.
To do so, we now rescale our matrix by this principle eigenvalue so that the largest eigenvalue is instead now just one.
Let us see what happens in this case.
-->

Từ phần thảo luận trên, lúc này ta kết luận rằng ta không hề muốn một vector ngẫu nhiên bị dãn hoặc co mất,
mà ta muốn vector ngẫu nhiên giữ nguyên kích thước trong suốt toàn bộ quá trình.
Để làm được điều đó, ta cần tái tỉ lệ ma trận bằng cách chia cho trị riêng chính, tức sao cho trị riêng lớn nhất giờ có giá trị 1.
Hãy xem chuyện gì sẽ xảy ra trong trường hợp này.


```{.python .input}
# Rescale the matrix `A`
A /= norm_eigs[-1]

# Do the same experiment again
v_in = np.random.randn(k, 1)

norm_list = [np.linalg.norm(v_in)]
for i in range(1, 100):
    v_in = A.dot(v_in)
    norm_list.append(np.linalg.norm(v_in))

d2l.plot(np.arange(0, 100), norm_list, 'Iteration', 'Value')
```

```{.python .input}
#@tab pytorch
# Rescale the matrix `A`
A /= norm_eigs[-1]

# Do the same experiment again
v_in = torch.randn(k, 1, dtype=torch.float64)

norm_list = [torch.norm(v_in).item()]
for i in range(1, 100):
    v_in = A @ v_in
    norm_list.append(torch.norm(v_in).item())

d2l.plot(torch.arange(0, 100), norm_list, 'Iteration', 'Value')
```

```{.python .input}
#@tab tensorflow
# Rescale the matrix `A`
A /= norm_eigs[-1]

# Do the same experiment again
v_in = tf.random.normal((k, 1), dtype=tf.float64)

norm_list = [tf.norm(v_in).numpy()]
for i in range(1, 100):
    v_in = tf.matmul(A, v_in)
    norm_list.append(tf.norm(v_in).numpy())

d2l.plot(tf.range(0, 100), norm_list, 'Iteration', 'Value')
```


<!--
We can also plot the ratio between consecutive norms as before and see that indeed it stabilizes.
-->

Ta cũng có thể biểu diễn tỉ lệ các chuẩn liên tục so với trước và xem liệu rằng nó có ổn định.

<!-- ===================== Kết thúc dịch Phần 6 ===================== -->

<!-- ===================== Bắt đầu dịch Phần 7 ===================== -->

```{.python .input}
# Also plot the ratio
norm_ratio_list = []
for i in range(1, 100):
    norm_ratio_list.append(norm_list[i]/norm_list[i-1])

d2l.plot(np.arange(1, 100), norm_ratio_list, 'Iteration', 'Ratio')
```

```{.python .input}
#@tab pytorch
# Also plot the ratio
norm_ratio_list = []
for i in range(1, 100):
    norm_ratio_list.append(norm_list[i]/norm_list[i-1])

d2l.plot(torch.arange(1, 100), norm_ratio_list, 'Iteration', 'Ratio')
```

```{.python .input}
#@tab tensorflow
# Also plot the ratio
norm_ratio_list = []
for i in range(1, 100):
    norm_ratio_list.append(norm_list[i]/norm_list[i-1])

d2l.plot(tf.range(1, 100), norm_ratio_list, 'Iteration', 'Ratio')
```

## Kết lại

<!--
We now see exactly what we hoped for!
After normalizing the matrices by the principle eigenvalue, we see that the random data does not explode as before,
but rather eventually equilibrates to a specific value.
It would be nice to be able to do these things from first principles, and it turns out that if we look deeply at the mathematics of it,
we can see that the largest eigenvalue of a large random matrix with independent mean zero, 
variance one Gaussian entries is on average about $\sqrt{n}$, or in our case $\sqrt{5} \approx 2.2$,
due to a fascinating fact known as the *circular law* :cite:`Ginibre.1965`.
The relationship between the eigenvalues (and a related object called singular values) of random matrices 
has been shown to have deep connections to proper initialization of neural networks as was discussed in :cite:`Pennington.Schoenholz.Ganguli.2017` and subsequent works.
-->

Giờ ta có thể thấy được điều mà ta mong muốn!
Sau khi chuẩn hoá ma trận bằng trị riêng chính, ta thấy rằng dữ liệu ngẫu nhiên không còn bùng nổ như trước nữa,
thay vào đó lại cân bằng quanh một giá trị nhất định.
Sẽ thật tuyệt nếu ta có thể thực hiện việc này bằng các định đề cơ bản, và hoá ra là nếu ta tìm hiểu sâu về mặt toán học của nó,
ta có thể thấy rằng trị riêng lớn nhất của một ma trận lớn ngẫu nhiên theo phân phối Gauss, với kỳ vọng độc lập bằng 0,
phương sai bằng 1, về trung bình sẽ xấp xỉ bằng $\sqrt{n}$, hay trong trường hợp của ta là $\sqrt{5} \approx 2.2$,
tuân theo một luật tuyệt vời là *luật vòng tròn (circular law)* :cite:`Ginibre.1965`.
Mối quan hệ giữa các trị riêng (và một đại lượng liên quan được gọi là trị đơn (*singular value*)) của ma trận ngẫu nhiên
đã được chứng minh là có liên hệ sâu sắc tới việc khởi tạo mạng nơ-ron một cách thích hợp như đã thảo luận trong :cite:`Pennington.Schoenholz.Ganguli.2017` và các nghiên cứu liên quan.


## Tóm tắt

<!--
* Eigenvectors are vectors which are stretched by a matrix without changing direction.
* Eigenvalues are the amount that the eigenvectors are stretched by the application of the matrix.
* The eigendecomposition of a matrix can allow for many operations to be reduced to operations on the eigenvalues.
* The Gershgorin Circle Theorem can provide approximate values for the eigenvalues of a matrix.
* The behavior of iterated matrix powers depends primarily on the size of the largest eigenvalue.  This understanding has many applications in the theory of neural network initialization.
-->

* Vector riêng là các vector bị dãn bởi một ma trận mà không thay đổi hướng.
* Trị riêng là mức độ mà các vector riêng đó bị dãn bởi khai triển ma trận.
* Phân tích trị riêng của ma trận cho phép nhiều thao tác trên ma trận có thể rút gọn thành các thao tác trên trị riêng.
* Định lý Đường tròn Gershgorin (*Gershgorin Circle Theorem*) có thể cung cấp giá trị xấp xỉ cho các trị riêng của một ma trận.
* Hành vi của lặp lũy thừa cho ma trận chủ yếu phụ thuộc vào độ lớn của trị riêng lớn nhất. Điều này có rất nhiều ứng dụng trong lý thuyết khởi tạo cho mạng nơ-ron.


## Bài tập

<!--
1. What are the eigenvalues and eigenvectors of
-->

1. Tìm các trị riêng và vector riêng của


$$
\mathbf{A} = \begin{bmatrix}
2 & 1 \\
1 & 2
\end{bmatrix}?
$$


<!--
2. What are the eigenvalues and eigenvectors of the following matrix, and what is strange about this example compared to the previous one?
-->

2. Tìm các trị riêng và vector riêng của ma trận sau đây, và cho biết có điều gì lạ ở ví dụ này so với ví dụ trước?


$$
\mathbf{A} = \begin{bmatrix}
2 & 1 \\
0 & 2
\end{bmatrix}.
$$


<!--
3. Without computing the eigenvalues, is it possible that the smallest eigenvalue of the following matrix is less that $0.5$? 
*Note*: this problem can be done in your head.
-->

3. Không tính các trị riêng, liệu có khả năng trị riêng nhỏ nhất của ma trận sau nhỏ hơn $0.5$?
*Ghi chú*: bài tập này có thể nhẩm được trong đầu.


<!-- ===================== Kết thúc dịch Phần 7 ===================== -->
<!-- ========================================= REVISE PHẦN 2 - KẾT THÚC ===================================-->


$$
\mathbf{A} = \begin{bmatrix}
3.0 & 0.1 & 0.3 & 1.0 \\
0.1 & 1.0 & 0.1 & 0.2 \\
0.3 & 0.1 & 5.0 & 0.0 \\
1.0 & 0.2 & 0.0 & 1.8
\end{bmatrix}.
$$


## Thảo luận
* Tiếng Anh: [MXNet](https://discuss.d2l.ai/t/411)
* Tiếng Việt: [Diễn đàn Machine Learning Cơ Bản](https://forum.machinelearningcoban.com/c/d2l)


## Những người thực hiện
Bản dịch trong trang này được thực hiện bởi:
<!--
Tác giả của mỗi Pull Request điền tên mình và tên những người review mà bạn thấy
hữu ích vào từng phần tương ứng. Mỗi dòng một tên, bắt đầu bằng dấu `*`.

Tên đầy đủ của các reviewer có thể được tìm thấy tại https://github.com/aivivn/d2l-vn/blob/master/docs/contributors_info.md
-->

* Đoàn Võ Duy Thanh
<!-- Phần 1 -->
* Trần Yến Thy
* Nguyễn Văn Cường

<!-- Phần 2 -->
* Trần Yến Thy
* Nguyễn Văn Cường

<!-- Phần 3 -->
* Trần Yến Thy
* Nguyễn Văn Cường

<!-- Phần 4 -->
* Trần Yến Thy
* Nguyễn Văn Cường

<!-- Phần 5 -->
* Đỗ Trường Giang

<!-- Phần 6 -->
* Đỗ Trường Giang

<!-- Phần 7 -->
* Đỗ Trường Giang


*Lần cập nhật gần nhất: 10/09/2020. (Cập nhật lần cuối từ nội dung gốc: 24/07/2020)*
