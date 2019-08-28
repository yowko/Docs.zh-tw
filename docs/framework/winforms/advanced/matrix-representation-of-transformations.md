---
title: 以矩陣來表示轉換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- composite transformations
- transformations [Windows Forms], linear
- matrices
- translations in matrix representation
- transformations [Windows Forms], composite
- vectors
- linear transformations
- transformations [Windows Forms], matrix representation of
- transformations [Windows Forms], translation
- affine transformations
ms.assetid: 0659fe00-9e0c-41c4-9118-016f2404c905
ms.openlocfilehash: 24da407de24a924a68466e4301cc3f4a74cb2e94
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044244"
---
# <a name="matrix-representation-of-transformations"></a><span data-ttu-id="ce64d-102">以矩陣來表示轉換</span><span class="sxs-lookup"><span data-stu-id="ce64d-102">Matrix Representation of Transformations</span></span>
<span data-ttu-id="ce64d-103">M × n 矩陣是以 m 列和 n 個數據行排列的一組數位。</span><span class="sxs-lookup"><span data-stu-id="ce64d-103">An m×n matrix is a set of numbers arranged in m rows and n columns.</span></span> <span data-ttu-id="ce64d-104">下圖顯示數個矩陣。</span><span class="sxs-lookup"><span data-stu-id="ce64d-104">The following illustration shows several matrices.</span></span>  
  
 <span data-ttu-id="ce64d-105">![Transformations](./media/aboutgdip05-art04.gif "AboutGdip05_art04")</span><span class="sxs-lookup"><span data-stu-id="ce64d-105">![Transformations](./media/aboutgdip05-art04.gif "AboutGdip05_art04")</span></span>  
  
 <span data-ttu-id="ce64d-106">您可以藉由加入個別元素, 加入相同大小的兩個矩陣。</span><span class="sxs-lookup"><span data-stu-id="ce64d-106">You can add two matrices of the same size by adding individual elements.</span></span> <span data-ttu-id="ce64d-107">下圖顯示兩個矩陣加法的範例。</span><span class="sxs-lookup"><span data-stu-id="ce64d-107">The following illustration shows two examples of matrix addition.</span></span>  
  
 <span data-ttu-id="ce64d-108">![Transformations](./media/aboutgdip05-art05.gif "AboutGdip05_art05")</span><span class="sxs-lookup"><span data-stu-id="ce64d-108">![Transformations](./media/aboutgdip05-art05.gif "AboutGdip05_art05")</span></span>  
  
 <span data-ttu-id="ce64d-109">M × n 矩陣可以乘以 n × p 矩陣, 而結果則是 m × p 矩陣。</span><span class="sxs-lookup"><span data-stu-id="ce64d-109">An m×n matrix can be multiplied by an n×p matrix, and the result is an m×p matrix.</span></span> <span data-ttu-id="ce64d-110">第一個矩陣中的資料行數目必須與第二個矩陣中的資料列數目相同。</span><span class="sxs-lookup"><span data-stu-id="ce64d-110">The number of columns in the first matrix must be the same as the number of rows in the second matrix.</span></span> <span data-ttu-id="ce64d-111">例如, 4 ×2矩陣可以乘以2×3矩陣, 以產生4×3矩陣。</span><span class="sxs-lookup"><span data-stu-id="ce64d-111">For example, a 4×2 matrix can be multiplied by a 2×3 matrix to produce a 4×3 matrix.</span></span>  
  
 <span data-ttu-id="ce64d-112">平面中的點和矩陣的資料列和資料行可以視為向量。</span><span class="sxs-lookup"><span data-stu-id="ce64d-112">Points in the plane and rows and columns of a matrix can be thought of as vectors.</span></span> <span data-ttu-id="ce64d-113">例如, (2, 5) 是包含兩個元件的向量, 而 (3, 7, 1) 是包含三個元件的向量。</span><span class="sxs-lookup"><span data-stu-id="ce64d-113">For example, (2, 5) is a vector with two components, and (3, 7, 1) is a vector with three components.</span></span> <span data-ttu-id="ce64d-114">兩個向量的點乘積定義如下:</span><span class="sxs-lookup"><span data-stu-id="ce64d-114">The dot product of two vectors is defined as follows:</span></span>  
  
 <span data-ttu-id="ce64d-115">(a, b) • (c, d) = ac + bd</span><span class="sxs-lookup"><span data-stu-id="ce64d-115">(a, b) • (c, d) = ac + bd</span></span>  
  
 <span data-ttu-id="ce64d-116">(a、b、c) • (d, e, f) = ad + 是 + cf</span><span class="sxs-lookup"><span data-stu-id="ce64d-116">(a, b, c) • (d, e, f) = ad + be + cf</span></span>  
  
 <span data-ttu-id="ce64d-117">例如, (2, 3) 和 (5, 4) 的點乘積為 (2) (5) + (3) (4) = 22。</span><span class="sxs-lookup"><span data-stu-id="ce64d-117">For example, the dot product of (2, 3) and (5, 4) is (2)(5) + (3)(4) = 22.</span></span> <span data-ttu-id="ce64d-118">(2, 5, 1) 和 (4, 3, 1) 的點乘積為 (2) (4) + (5) (3) + (1) (1) = 24。</span><span class="sxs-lookup"><span data-stu-id="ce64d-118">The dot product of (2, 5, 1) and (4, 3, 1) is (2)(4) + (5)(3) + (1)(1) = 24.</span></span> <span data-ttu-id="ce64d-119">請注意, 兩個向量的點乘積是一個數位, 而不是另一個向量。</span><span class="sxs-lookup"><span data-stu-id="ce64d-119">Note that the dot product of two vectors is a number, not another vector.</span></span> <span data-ttu-id="ce64d-120">另請注意, 只有當兩個向量具有相同數目的元件時, 您才可以計算網點乘積。</span><span class="sxs-lookup"><span data-stu-id="ce64d-120">Also note that you can calculate the dot product only if the two vectors have the same number of components.</span></span>  
  
 <span data-ttu-id="ce64d-121">讓 (i, j) 成為第 i 個數據列和第 j 個數據行中 [矩陣 A] 的專案。</span><span class="sxs-lookup"><span data-stu-id="ce64d-121">Let A(i, j) be the entry in matrix A in the ith row and the jth column.</span></span> <span data-ttu-id="ce64d-122">例如, (3, 2) 是第3列和第2個數據行之矩陣 A 中的專案。</span><span class="sxs-lookup"><span data-stu-id="ce64d-122">For example A(3, 2) is the entry in matrix A in the 3rd row and the 2nd column.</span></span> <span data-ttu-id="ce64d-123">假設 A、B 和 C 是矩陣, 而 AB = C。C 的專案計算方式如下:</span><span class="sxs-lookup"><span data-stu-id="ce64d-123">Suppose A, B, and C are matrices, and AB = C. The entries of C are calculated as follows:</span></span>  
  
 <span data-ttu-id="ce64d-124">C (i, j) = (資料列 i) • (B 的資料行 j)</span><span class="sxs-lookup"><span data-stu-id="ce64d-124">C(i, j) = (row i of A) • (column j of B)</span></span>  
  
 <span data-ttu-id="ce64d-125">下圖顯示數個矩陣乘法的範例。</span><span class="sxs-lookup"><span data-stu-id="ce64d-125">The following illustration shows several examples of matrix multiplication.</span></span>  
  
 <span data-ttu-id="ce64d-126">![Transformations](./media/aboutgdip05-art06.gif "AboutGdip05_art06")</span><span class="sxs-lookup"><span data-stu-id="ce64d-126">![Transformations](./media/aboutgdip05-art06.gif "AboutGdip05_art06")</span></span>  
  
 <span data-ttu-id="ce64d-127">如果您想要將平面中的某個點視為1×2矩陣, 可以將該點乘以2×2矩陣來進行轉換。</span><span class="sxs-lookup"><span data-stu-id="ce64d-127">If you think of a point in a plane as a 1×2 matrix, you can transform that point by multiplying it by a 2×2 matrix.</span></span> <span data-ttu-id="ce64d-128">下圖顯示數個套用至點的轉換 (2, 1)。</span><span class="sxs-lookup"><span data-stu-id="ce64d-128">The following illustration shows several transformations applied to the point (2, 1).</span></span>  
  
 <span data-ttu-id="ce64d-129">![Transformations](./media/aboutgdip05-art07.gif "AboutGdip05_art07")</span><span class="sxs-lookup"><span data-stu-id="ce64d-129">![Transformations](./media/aboutgdip05-art07.gif "AboutGdip05_art07")</span></span>  
  
 <span data-ttu-id="ce64d-130">上圖中顯示的所有轉換都是線性轉換。</span><span class="sxs-lookup"><span data-stu-id="ce64d-130">All of the transformations shown in the preceding figure are linear transformations.</span></span> <span data-ttu-id="ce64d-131">某些其他轉換 (例如轉譯) 不是線性的, 而且無法以2×2矩陣的乘法表示。</span><span class="sxs-lookup"><span data-stu-id="ce64d-131">Certain other transformations, such as translation, are not linear, and cannot be expressed as multiplication by a 2×2 matrix.</span></span> <span data-ttu-id="ce64d-132">假設您想要從點 (2, 1) 開始, 旋轉90度, 將 x 方向轉譯為3個單位, 然後在 y 方向轉譯為4個單位。</span><span class="sxs-lookup"><span data-stu-id="ce64d-132">Suppose you want to start with the point (2, 1), rotate it 90 degrees, translate it 3 units in the x direction, and translate it 4 units in the y direction.</span></span> <span data-ttu-id="ce64d-133">您可以使用矩陣乘法, 再加上矩陣加法來完成這項操作。</span><span class="sxs-lookup"><span data-stu-id="ce64d-133">You can accomplish this by using a matrix multiplication followed by a matrix addition.</span></span>  
  
 <span data-ttu-id="ce64d-134">![Transformations](./media/aboutgdip05-art08.gif "AboutGdip05_art08")</span><span class="sxs-lookup"><span data-stu-id="ce64d-134">![Transformations](./media/aboutgdip05-art08.gif "AboutGdip05_art08")</span></span>  
  
 <span data-ttu-id="ce64d-135">線性轉換 (乘以2×2矩陣) 後面接著平移 (加入1×2矩陣) 稱為「仿射」轉換。</span><span class="sxs-lookup"><span data-stu-id="ce64d-135">A linear transformation (multiplication by a 2×2 matrix) followed by a translation (addition of a 1×2 matrix) is called an affine transformation.</span></span> <span data-ttu-id="ce64d-136">另一個方法是在一對矩陣中儲存仿射轉換 (一個用於線性部分, 另一個用於轉譯), 是將整個轉換儲存在3×3矩陣中。</span><span class="sxs-lookup"><span data-stu-id="ce64d-136">An alternative to storing an affine transformation in a pair of matrices (one for the linear part and one for the translation) is to store the entire transformation in a 3×3 matrix.</span></span> <span data-ttu-id="ce64d-137">若要進行這項作業, 平面中的點必須儲存在具有虛擬3座標的1×3矩陣中。</span><span class="sxs-lookup"><span data-stu-id="ce64d-137">To make this work, a point in the plane must be stored in a 1×3 matrix with a dummy 3rd coordinate.</span></span> <span data-ttu-id="ce64d-138">一般的技巧是讓所有的第3個座標都等於1。</span><span class="sxs-lookup"><span data-stu-id="ce64d-138">The usual technique is to make all 3rd coordinates equal to 1.</span></span> <span data-ttu-id="ce64d-139">例如, 點 (2, 1) 是以矩陣 [2 1 1] 表示。</span><span class="sxs-lookup"><span data-stu-id="ce64d-139">For example, the point (2, 1) is represented by the matrix [2 1 1].</span></span> <span data-ttu-id="ce64d-140">下圖顯示仿射轉換 (旋轉90度; 以 x 方向轉譯3個單位, y 方向為4個單位), 以乘單一3×3矩陣的方式來表示。</span><span class="sxs-lookup"><span data-stu-id="ce64d-140">The following illustration shows an affine transformation (rotate 90 degrees; translate 3 units in the x direction, 4 units in the y direction) expressed as multiplication by a single 3×3 matrix.</span></span>  
  
 <span data-ttu-id="ce64d-141">![Transformations](./media/aboutgdip05-art09.gif "AboutGdip05_art09")</span><span class="sxs-lookup"><span data-stu-id="ce64d-141">![Transformations](./media/aboutgdip05-art09.gif "AboutGdip05_art09")</span></span>  
  
 <span data-ttu-id="ce64d-142">在上述範例中, 點 (2, 1) 會對應到點 (2, 6)。</span><span class="sxs-lookup"><span data-stu-id="ce64d-142">In the preceding example, the point (2, 1) is mapped to the point (2, 6).</span></span> <span data-ttu-id="ce64d-143">請注意, 3 ×3矩陣的第三個數據行包含數位 0, 0, 1。</span><span class="sxs-lookup"><span data-stu-id="ce64d-143">Note that the third column of the 3×3 matrix contains the numbers 0, 0, 1.</span></span> <span data-ttu-id="ce64d-144">這一律是仿射轉換的3×3矩陣的情況。</span><span class="sxs-lookup"><span data-stu-id="ce64d-144">This will always be the case for the 3×3 matrix of an affine transformation.</span></span> <span data-ttu-id="ce64d-145">重要數位是資料行1和2中的六個數字。</span><span class="sxs-lookup"><span data-stu-id="ce64d-145">The important numbers are the six numbers in columns 1 and 2.</span></span> <span data-ttu-id="ce64d-146">矩陣的左上2×2部分代表轉換的線性部分, 而第三個數據列中的前兩個專案代表轉譯。</span><span class="sxs-lookup"><span data-stu-id="ce64d-146">The upper-left 2×2 portion of the matrix represents the linear part of the transformation, and the first two entries in the 3rd row represent the translation.</span></span>  
  
 <span data-ttu-id="ce64d-147">![Transformations](./media/aboutgdip05-art10.gif "AboutGdip05_art10")</span><span class="sxs-lookup"><span data-stu-id="ce64d-147">![Transformations](./media/aboutgdip05-art10.gif "AboutGdip05_art10")</span></span>  
  
 <span data-ttu-id="ce64d-148">在 gdi + 中, 您可以將仿射<xref:System.Drawing.Drawing2D.Matrix>轉換儲存在物件中。</span><span class="sxs-lookup"><span data-stu-id="ce64d-148">In GDI+ you can store an affine transformation in a <xref:System.Drawing.Drawing2D.Matrix> object.</span></span> <span data-ttu-id="ce64d-149">因為代表仿射轉換之矩陣的第三個數據行一律是 (0, 0, 1), 所以您在建立<xref:System.Drawing.Drawing2D.Matrix>物件時, 只會在前兩個數據行中指定六個數字。</span><span class="sxs-lookup"><span data-stu-id="ce64d-149">Because the third column of a matrix that represents an affine transformation is always (0, 0, 1), you specify only the six numbers in the first two columns when you construct a <xref:System.Drawing.Drawing2D.Matrix> object.</span></span> <span data-ttu-id="ce64d-150">語句`Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)`會結構如上圖所示的矩陣。</span><span class="sxs-lookup"><span data-stu-id="ce64d-150">The statement `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` constructs the matrix shown in the preceding figure.</span></span>  
  
## <a name="composite-transformations"></a><span data-ttu-id="ce64d-151">複合轉換</span><span class="sxs-lookup"><span data-stu-id="ce64d-151">Composite Transformations</span></span>  
 <span data-ttu-id="ce64d-152">複合轉換是一系列的轉換, 再接著另一個。</span><span class="sxs-lookup"><span data-stu-id="ce64d-152">A composite transformation is a sequence of transformations, one followed by the other.</span></span> <span data-ttu-id="ce64d-153">請考慮下列清單中的矩陣和轉換:</span><span class="sxs-lookup"><span data-stu-id="ce64d-153">Consider the matrices and transformations in the following list:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce64d-154">矩陣 A</span><span class="sxs-lookup"><span data-stu-id="ce64d-154">Matrix A</span></span>|<span data-ttu-id="ce64d-155">旋轉90度</span><span class="sxs-lookup"><span data-stu-id="ce64d-155">Rotate 90 degrees</span></span>|  
|<span data-ttu-id="ce64d-156">矩陣 B</span><span class="sxs-lookup"><span data-stu-id="ce64d-156">Matrix B</span></span>|<span data-ttu-id="ce64d-157">以 x 方向的2因數來縮放</span><span class="sxs-lookup"><span data-stu-id="ce64d-157">Scale by a factor of 2 in the x direction</span></span>|  
|<span data-ttu-id="ce64d-158">矩陣 C</span><span class="sxs-lookup"><span data-stu-id="ce64d-158">Matrix C</span></span>|<span data-ttu-id="ce64d-159">以 y 方向轉譯3個單位</span><span class="sxs-lookup"><span data-stu-id="ce64d-159">Translate 3 units in the y direction</span></span>|  
  
 <span data-ttu-id="ce64d-160">如果一開始是以矩陣 [2 1 1] 表示的點 (2, 1), 然後乘以 A、B、C, 則點 (2, 1) 會依照列出的順序進行三個轉換。</span><span class="sxs-lookup"><span data-stu-id="ce64d-160">If we start with the point (2, 1) — represented by the matrix [2 1 1] — and multiply by A, then B, then C, the point (2, 1) will undergo the three transformations in the order listed.</span></span>  
  
 <span data-ttu-id="ce64d-161">[2 1 1]ABC = [-2 5 1]</span><span class="sxs-lookup"><span data-stu-id="ce64d-161">[2 1 1]ABC = [-2 5 1]</span></span>  
  
 <span data-ttu-id="ce64d-162">與其將複合轉換的三個部分儲存在三個不同的矩陣中, 您可以將 A、B 和 C 相乘, 以取得儲存整個複合轉換的單一3×3矩陣。</span><span class="sxs-lookup"><span data-stu-id="ce64d-162">Rather than store the three parts of the composite transformation in three separate matrices, you can multiply A, B, and C together to get a single 3×3 matrix that stores the entire composite transformation.</span></span> <span data-ttu-id="ce64d-163">假設 ABC = D。然後乘以 D 的點會得到與點相乘的結果, 再乘以 B, 然後 C。</span><span class="sxs-lookup"><span data-stu-id="ce64d-163">Suppose ABC = D. Then a point multiplied by D gives the same result as a point multiplied by A, then B, then C.</span></span>  
  
 <span data-ttu-id="ce64d-164">[2 1 1]D = [-2 5 1]</span><span class="sxs-lookup"><span data-stu-id="ce64d-164">[2 1 1]D = [-2 5 1]</span></span>  
  
 <span data-ttu-id="ce64d-165">下圖顯示矩陣 A、B、C 和 D。</span><span class="sxs-lookup"><span data-stu-id="ce64d-165">The following illustration shows the matrices A, B, C, and D.</span></span>  
  
 <span data-ttu-id="ce64d-166">![Transformations](./media/aboutgdip05-art12.gif "AboutGdip05_art12")</span><span class="sxs-lookup"><span data-stu-id="ce64d-166">![Transformations](./media/aboutgdip05-art12.gif "AboutGdip05_art12")</span></span>  
  
 <span data-ttu-id="ce64d-167">複合轉換的矩陣可以藉由乘以個別轉換矩陣來形成, 這表示任何仿射轉換的順序都可以儲存在單一<xref:System.Drawing.Drawing2D.Matrix>物件中。</span><span class="sxs-lookup"><span data-stu-id="ce64d-167">The fact that the matrix of a composite transformation can be formed by multiplying the individual transformation matrices means that any sequence of affine transformations can be stored in a single <xref:System.Drawing.Drawing2D.Matrix> object.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="ce64d-168">複合轉換的順序很重要。</span><span class="sxs-lookup"><span data-stu-id="ce64d-168">The order of a composite transformation is important.</span></span> <span data-ttu-id="ce64d-169">在 [一般] 中, [旋轉]、[調整]、[轉譯] 和 [縮放] 不同, 然後旋轉, 然後平移。</span><span class="sxs-lookup"><span data-stu-id="ce64d-169">In general, rotate, then scale, then translate is not the same as scale, then rotate, then translate.</span></span> <span data-ttu-id="ce64d-170">同樣地, 矩陣乘法的順序也很重要。</span><span class="sxs-lookup"><span data-stu-id="ce64d-170">Similarly, the order of matrix multiplication is important.</span></span> <span data-ttu-id="ce64d-171">一般來說, ABC 與 k 不同。</span><span class="sxs-lookup"><span data-stu-id="ce64d-171">In general, ABC is not the same as BAC.</span></span>  
  
 <span data-ttu-id="ce64d-172"><xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A> <xref:System.Drawing.Drawing2D.Matrix.Translate%2A> <xref:System.Drawing.Drawing2D.Matrix.Scale%2A> <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A> <xref:System.Drawing.Drawing2D.Matrix.Shear%2A> <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>類別提供數種方法來建立複合轉換:、、、、和。 <xref:System.Drawing.Drawing2D.Matrix></span><span class="sxs-lookup"><span data-stu-id="ce64d-172">The <xref:System.Drawing.Drawing2D.Matrix> class provides several methods for building a composite transformation: <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>, <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>, <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>, <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>, <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>, and <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>.</span></span> <span data-ttu-id="ce64d-173">下列範例會建立複合轉換的矩陣, 其會先旋轉30度, 然後在 y 方向以2的因數來縮放, 然後在 x 方向轉譯5個單位:</span><span class="sxs-lookup"><span data-stu-id="ce64d-173">The following example creates the matrix of a composite transformation that first rotates 30 degrees, then scales by a factor of 2 in the y direction, and then translates 5 units in the x direction:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 <span data-ttu-id="ce64d-174">下圖顯示矩陣。</span><span class="sxs-lookup"><span data-stu-id="ce64d-174">The following illustration shows the matrix.</span></span>  
  
 <span data-ttu-id="ce64d-175">![Transformations](./media/aboutgdip05-art13.gif "AboutGdip05_art13")</span><span class="sxs-lookup"><span data-stu-id="ce64d-175">![Transformations](./media/aboutgdip05-art13.gif "AboutGdip05_art13")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce64d-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce64d-176">See also</span></span>

- [<span data-ttu-id="ce64d-177">座標系統和轉換</span><span class="sxs-lookup"><span data-stu-id="ce64d-177">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
- [<span data-ttu-id="ce64d-178">使用 Managed GDI+ 中的轉換</span><span class="sxs-lookup"><span data-stu-id="ce64d-178">Using Transformations in Managed GDI+</span></span>](using-transformations-in-managed-gdi.md)
