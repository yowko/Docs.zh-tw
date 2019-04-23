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
ms.openlocfilehash: c87be8eaf715e373da75dd8f91889b0e396dba0d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172779"
---
# <a name="matrix-representation-of-transformations"></a><span data-ttu-id="c457a-102">以矩陣來表示轉換</span><span class="sxs-lookup"><span data-stu-id="c457a-102">Matrix Representation of Transformations</span></span>
<span data-ttu-id="c457a-103">M × n 矩陣是一組在億個資料列和 n 個資料行中排列的數字。</span><span class="sxs-lookup"><span data-stu-id="c457a-103">An m×n matrix is a set of numbers arranged in m rows and n columns.</span></span> <span data-ttu-id="c457a-104">下圖顯示數個矩陣。</span><span class="sxs-lookup"><span data-stu-id="c457a-104">The following illustration shows several matrices.</span></span>  
  
 <span data-ttu-id="c457a-105">![Transformations](./media/aboutgdip05-art04.gif "AboutGdip05_art04")</span><span class="sxs-lookup"><span data-stu-id="c457a-105">![Transformations](./media/aboutgdip05-art04.gif "AboutGdip05_art04")</span></span>  
  
 <span data-ttu-id="c457a-106">您可以藉由新增個別的項目加入相同大小的兩個矩陣。</span><span class="sxs-lookup"><span data-stu-id="c457a-106">You can add two matrices of the same size by adding individual elements.</span></span> <span data-ttu-id="c457a-107">下圖顯示兩個矩陣新增範例。</span><span class="sxs-lookup"><span data-stu-id="c457a-107">The following illustration shows two examples of matrix addition.</span></span>  
  
 <span data-ttu-id="c457a-108">![Transformations](./media/aboutgdip05-art05.gif "AboutGdip05_art05")</span><span class="sxs-lookup"><span data-stu-id="c457a-108">![Transformations](./media/aboutgdip05-art05.gif "AboutGdip05_art05")</span></span>  
  
 <span data-ttu-id="c457a-109">M × n 矩陣乘以 n × p 矩陣，且結果為 m × p 矩陣。</span><span class="sxs-lookup"><span data-stu-id="c457a-109">An m×n matrix can be multiplied by an n×p matrix, and the result is an m×p matrix.</span></span> <span data-ttu-id="c457a-110">第一個矩陣中的資料行數目必須是第二個矩陣中的資料列數目相同。</span><span class="sxs-lookup"><span data-stu-id="c457a-110">The number of columns in the first matrix must be the same as the number of rows in the second matrix.</span></span> <span data-ttu-id="c457a-111">例如，4 × 2 的矩陣可以乘以 2 的 × 3 矩陣，以產生 4 × 3 的矩陣。</span><span class="sxs-lookup"><span data-stu-id="c457a-111">For example, a 4×2 matrix can be multiplied by a 2×3 matrix to produce a 4×3 matrix.</span></span>  
  
 <span data-ttu-id="c457a-112">在平面和資料列和資料行的矩陣中的點可以視為向量。</span><span class="sxs-lookup"><span data-stu-id="c457a-112">Points in the plane and rows and columns of a matrix can be thought of as vectors.</span></span> <span data-ttu-id="c457a-113">例如，（2，5） 是具有兩個元件的向量和 （3，7，1） 是具有三個元件的向量。</span><span class="sxs-lookup"><span data-stu-id="c457a-113">For example, (2, 5) is a vector with two components, and (3, 7, 1) is a vector with three components.</span></span> <span data-ttu-id="c457a-114">兩個向量的內積定義，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c457a-114">The dot product of two vectors is defined as follows:</span></span>  
  
 <span data-ttu-id="c457a-115">(a、 b） • (c，d) = ac + bd</span><span class="sxs-lookup"><span data-stu-id="c457a-115">(a, b) • (c, d) = ac + bd</span></span>  
  
 <span data-ttu-id="c457a-116">(a、 b、 c） • （d，e，f） = ad + 是 + cf</span><span class="sxs-lookup"><span data-stu-id="c457a-116">(a, b, c) • (d, e, f) = ad + be + cf</span></span>  
  
 <span data-ttu-id="c457a-117">比方說，積 （2、 3） 和 （5，4） 是 (2)(5) + (3)(4) = 22。</span><span class="sxs-lookup"><span data-stu-id="c457a-117">For example, the dot product of (2, 3) and (5, 4) is (2)(5) + (3)(4) = 22.</span></span> <span data-ttu-id="c457a-118">積 （2，5，1） 和 （4，3，1） 是 (2)(4) + (5)(3) + (1)(1) = 24。</span><span class="sxs-lookup"><span data-stu-id="c457a-118">The dot product of (2, 5, 1) and (4, 3, 1) is (2)(4) + (5)(3) + (1)(1) = 24.</span></span> <span data-ttu-id="c457a-119">請注意，兩個向量的內積數字，而非另一個向量。</span><span class="sxs-lookup"><span data-stu-id="c457a-119">Note that the dot product of two vectors is a number, not another vector.</span></span> <span data-ttu-id="c457a-120">也請注意，您就可以計算積，只有當兩個向量擁有相同數目的元件。</span><span class="sxs-lookup"><span data-stu-id="c457a-120">Also note that you can calculate the dot product only if the two vectors have the same number of components.</span></span>  
  
 <span data-ttu-id="c457a-121">讓 A(i, j) 是矩陣的第 i 個資料列和第 j 個資料行中的項目。</span><span class="sxs-lookup"><span data-stu-id="c457a-121">Let A(i, j) be the entry in matrix A in the ith row and the jth column.</span></span> <span data-ttu-id="c457a-122">比方說的 （3，2） 是矩陣的第 3 個資料列和第 2 個資料行中的項目。</span><span class="sxs-lookup"><span data-stu-id="c457a-122">For example A(3, 2) is the entry in matrix A in the 3rd row and the 2nd column.</span></span> <span data-ttu-id="c457a-123">假設 A、 B 和 C 是矩陣和 AB = c。C 的項目計算，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c457a-123">Suppose A, B, and C are matrices, and AB = C. The entries of C are calculated as follows:</span></span>  
  
 <span data-ttu-id="c457a-124">C （i，j） = （資料列 i A） • （資料行 j B）</span><span class="sxs-lookup"><span data-stu-id="c457a-124">C(i, j) = (row i of A) • (column j of B)</span></span>  
  
 <span data-ttu-id="c457a-125">下圖矩陣相乘的數個的範例。</span><span class="sxs-lookup"><span data-stu-id="c457a-125">The following illustration shows several examples of matrix multiplication.</span></span>  
  
 <span data-ttu-id="c457a-126">![Transformations](./media/aboutgdip05-art06.gif "AboutGdip05_art06")</span><span class="sxs-lookup"><span data-stu-id="c457a-126">![Transformations](./media/aboutgdip05-art06.gif "AboutGdip05_art06")</span></span>  
  
 <span data-ttu-id="c457a-127">如果您將做為 1 的 × 2 矩陣平面中的點，您可以藉由將它乘以 2 × 2 矩陣來轉換該點。</span><span class="sxs-lookup"><span data-stu-id="c457a-127">If you think of a point in a plane as a 1×2 matrix, you can transform that point by multiplying it by a 2×2 matrix.</span></span> <span data-ttu-id="c457a-128">下圖顯示數個轉換套用到 （2，1） 的點。</span><span class="sxs-lookup"><span data-stu-id="c457a-128">The following illustration shows several transformations applied to the point (2, 1).</span></span>  
  
 <span data-ttu-id="c457a-129">![Transformations](./media/aboutgdip05-art07.gif "AboutGdip05_art07")</span><span class="sxs-lookup"><span data-stu-id="c457a-129">![Transformations](./media/aboutgdip05-art07.gif "AboutGdip05_art07")</span></span>  
  
 <span data-ttu-id="c457a-130">所有在上圖中顯示的轉換都是線性轉換。</span><span class="sxs-lookup"><span data-stu-id="c457a-130">All of the transformations shown in the preceding figure are linear transformations.</span></span> <span data-ttu-id="c457a-131">某些其他轉換，例如轉譯，而且非屬線性，不能表示為乘以 2 × 2 矩陣。</span><span class="sxs-lookup"><span data-stu-id="c457a-131">Certain other transformations, such as translation, are not linear, and cannot be expressed as multiplication by a 2×2 matrix.</span></span> <span data-ttu-id="c457a-132">假設您想要開始使用點 （2，1），旋轉 90 度、 將它轉譯成 3 個單位 x 方向和將其轉譯在 y 方向的 4 個單位。</span><span class="sxs-lookup"><span data-stu-id="c457a-132">Suppose you want to start with the point (2, 1), rotate it 90 degrees, translate it 3 units in the x direction, and translate it 4 units in the y direction.</span></span> <span data-ttu-id="c457a-133">您可以使用後面接著矩陣加入矩陣相乘來完成。</span><span class="sxs-lookup"><span data-stu-id="c457a-133">You can accomplish this by using a matrix multiplication followed by a matrix addition.</span></span>  
  
 <span data-ttu-id="c457a-134">![Transformations](./media/aboutgdip05-art08.gif "AboutGdip05_art08")</span><span class="sxs-lookup"><span data-stu-id="c457a-134">![Transformations](./media/aboutgdip05-art08.gif "AboutGdip05_art08")</span></span>  
  
 <span data-ttu-id="c457a-135">後面的翻譯 （加 1 × 2 矩陣的） 的線性轉換 （由 2 × 2 矩陣乘法） 稱為仿射轉換。</span><span class="sxs-lookup"><span data-stu-id="c457a-135">A linear transformation (multiplication by a 2×2 matrix) followed by a translation (addition of a 1×2 matrix) is called an affine transformation.</span></span> <span data-ttu-id="c457a-136">儲存仿射轉換矩陣 （一個為線性的一部分），做為轉換的一組中的替代方式是將整個轉換儲存 3 × 3 矩陣中。</span><span class="sxs-lookup"><span data-stu-id="c457a-136">An alternative to storing an affine transformation in a pair of matrices (one for the linear part and one for the translation) is to store the entire transformation in a 3×3 matrix.</span></span> <span data-ttu-id="c457a-137">若要讓這項工作，在平面的點必須儲存在與虛擬的第 3 個座標 1 × 3 的矩陣。</span><span class="sxs-lookup"><span data-stu-id="c457a-137">To make this work, a point in the plane must be stored in a 1×3 matrix with a dummy 3rd coordinate.</span></span> <span data-ttu-id="c457a-138">常用的技巧是讓所有的第 3 個座標等於 1。</span><span class="sxs-lookup"><span data-stu-id="c457a-138">The usual technique is to make all 3rd coordinates equal to 1.</span></span> <span data-ttu-id="c457a-139">例如，（2，1） 的點被以矩陣 [2 1 1]。</span><span class="sxs-lookup"><span data-stu-id="c457a-139">For example, the point (2, 1) is represented by the matrix [2 1 1].</span></span> <span data-ttu-id="c457a-140">下圖顯示仿射轉換 （旋轉 90 度; 轉譯在 x 方向的 3 個單位，在 y 方向的 4 個單位） 乘以 3 × 3 矩陣以表示。</span><span class="sxs-lookup"><span data-stu-id="c457a-140">The following illustration shows an affine transformation (rotate 90 degrees; translate 3 units in the x direction, 4 units in the y direction) expressed as multiplication by a single 3×3 matrix.</span></span>  
  
 <span data-ttu-id="c457a-141">![Transformations](./media/aboutgdip05-art09.gif "AboutGdip05_art09")</span><span class="sxs-lookup"><span data-stu-id="c457a-141">![Transformations](./media/aboutgdip05-art09.gif "AboutGdip05_art09")</span></span>  
  
 <span data-ttu-id="c457a-142">在上述範例中，點 （2，1） 會對應到點 （2，6）。</span><span class="sxs-lookup"><span data-stu-id="c457a-142">In the preceding example, the point (2, 1) is mapped to the point (2, 6).</span></span> <span data-ttu-id="c457a-143">請注意 3 × 3 矩陣的第三個資料行包含數字 0，0，1。</span><span class="sxs-lookup"><span data-stu-id="c457a-143">Note that the third column of the 3×3 matrix contains the numbers 0, 0, 1.</span></span> <span data-ttu-id="c457a-144">這一律會是 3 × 3 矩陣仿射轉換的情況。</span><span class="sxs-lookup"><span data-stu-id="c457a-144">This will always be the case for the 3×3 matrix of an affine transformation.</span></span> <span data-ttu-id="c457a-145">重要的數字是 1 和 2 的資料行中的六個數字。</span><span class="sxs-lookup"><span data-stu-id="c457a-145">The important numbers are the six numbers in columns 1 and 2.</span></span> <span data-ttu-id="c457a-146">矩陣的左上方 2 × 2 部分代表線性的組件的轉換，而第 3 個資料列中的前兩個項目代表轉譯。</span><span class="sxs-lookup"><span data-stu-id="c457a-146">The upper-left 2×2 portion of the matrix represents the linear part of the transformation, and the first two entries in the 3rd row represent the translation.</span></span>  
  
 <span data-ttu-id="c457a-147">![Transformations](./media/aboutgdip05-art10.gif "AboutGdip05_art10")</span><span class="sxs-lookup"><span data-stu-id="c457a-147">![Transformations](./media/aboutgdip05-art10.gif "AboutGdip05_art10")</span></span>  
  
 <span data-ttu-id="c457a-148">在 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]您可以儲存在仿射轉換<xref:System.Drawing.Drawing2D.Matrix>物件。</span><span class="sxs-lookup"><span data-stu-id="c457a-148">In [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you can store an affine transformation in a <xref:System.Drawing.Drawing2D.Matrix> object.</span></span> <span data-ttu-id="c457a-149">因為代表仿射轉換矩陣的第三個資料行一律是 （0，0，1），當您建構時，在前兩個資料行中指定的六個數字<xref:System.Drawing.Drawing2D.Matrix>物件。</span><span class="sxs-lookup"><span data-stu-id="c457a-149">Because the third column of a matrix that represents an affine transformation is always (0, 0, 1), you specify only the six numbers in the first two columns when you construct a <xref:System.Drawing.Drawing2D.Matrix> object.</span></span> <span data-ttu-id="c457a-150">陳述式`Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)`建構如上圖所示的矩陣。</span><span class="sxs-lookup"><span data-stu-id="c457a-150">The statement `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` constructs the matrix shown in the preceding figure.</span></span>  
  
## <a name="composite-transformations"></a><span data-ttu-id="c457a-151">複合轉換</span><span class="sxs-lookup"><span data-stu-id="c457a-151">Composite Transformations</span></span>  
 <span data-ttu-id="c457a-152">複合轉換是一連串的轉換，後面接著另一個。</span><span class="sxs-lookup"><span data-stu-id="c457a-152">A composite transformation is a sequence of transformations, one followed by the other.</span></span> <span data-ttu-id="c457a-153">請考慮下列清單中的轉換與矩陣：</span><span class="sxs-lookup"><span data-stu-id="c457a-153">Consider the matrices and transformations in the following list:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c457a-154">矩陣的</span><span class="sxs-lookup"><span data-stu-id="c457a-154">Matrix A</span></span>|<span data-ttu-id="c457a-155">旋轉 90 度</span><span class="sxs-lookup"><span data-stu-id="c457a-155">Rotate 90 degrees</span></span>|  
|<span data-ttu-id="c457a-156">矩陣 B</span><span class="sxs-lookup"><span data-stu-id="c457a-156">Matrix B</span></span>|<span data-ttu-id="c457a-157">在 x 方向的 2 倍縮放</span><span class="sxs-lookup"><span data-stu-id="c457a-157">Scale by a factor of 2 in the x direction</span></span>|  
|<span data-ttu-id="c457a-158">矩陣 C</span><span class="sxs-lookup"><span data-stu-id="c457a-158">Matrix C</span></span>|<span data-ttu-id="c457a-159">轉譯在 y 方向的 3 個單位</span><span class="sxs-lookup"><span data-stu-id="c457a-159">Translate 3 units in the y direction</span></span>|  
  
 <span data-ttu-id="c457a-160">如果我們開始點 （2，1） — 矩陣 [2 1 1] 表示的 — 並乘以 A，然後 B，則 C，（2，1） 的點將會進行三種轉換中列出的順序。</span><span class="sxs-lookup"><span data-stu-id="c457a-160">If we start with the point (2, 1) — represented by the matrix [2 1 1] — and multiply by A, then B, then C, the point (2, 1) will undergo the three transformations in the order listed.</span></span>  
  
 <span data-ttu-id="c457a-161">[2 1 1]ABC = [-2 5 1]</span><span class="sxs-lookup"><span data-stu-id="c457a-161">[2 1 1]ABC = [-2 5 1]</span></span>  
  
 <span data-ttu-id="c457a-162">而非 「 複合 」 轉換的三個部分儲存在三個個別的矩陣中，您可以將 A、 B 和 C 來取得儲存整個複合轉換單一 3 × 3 矩陣。</span><span class="sxs-lookup"><span data-stu-id="c457a-162">Rather than store the three parts of the composite transformation in three separate matrices, you can multiply A, B, and C together to get a single 3×3 matrix that stores the entire composite transformation.</span></span> <span data-ttu-id="c457a-163">假設 ABC = d。然後乘以 D 點會給予相同的結果為點乘以 A，然後 B，然後 c。</span><span class="sxs-lookup"><span data-stu-id="c457a-163">Suppose ABC = D. Then a point multiplied by D gives the same result as a point multiplied by A, then B, then C.</span></span>  
  
 <span data-ttu-id="c457a-164">[2 1 1]D = [-2 5 1]</span><span class="sxs-lookup"><span data-stu-id="c457a-164">[2 1 1]D = [-2 5 1]</span></span>  
  
 <span data-ttu-id="c457a-165">下圖顯示矩陣的 A、 B、 C 和 d。</span><span class="sxs-lookup"><span data-stu-id="c457a-165">The following illustration shows the matrices A, B, C, and D.</span></span>  
  
 <span data-ttu-id="c457a-166">![Transformations](./media/aboutgdip05-art12.gif "AboutGdip05_art12")</span><span class="sxs-lookup"><span data-stu-id="c457a-166">![Transformations](./media/aboutgdip05-art12.gif "AboutGdip05_art12")</span></span>  
  
 <span data-ttu-id="c457a-167">複合轉換矩陣可以依據個別的轉換矩陣相乘，這表示仿射轉換的任何序列都可以儲存在單一<xref:System.Drawing.Drawing2D.Matrix>物件。</span><span class="sxs-lookup"><span data-stu-id="c457a-167">The fact that the matrix of a composite transformation can be formed by multiplying the individual transformation matrices means that any sequence of affine transformations can be stored in a single <xref:System.Drawing.Drawing2D.Matrix> object.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c457a-168">複合轉換順序很重要。</span><span class="sxs-lookup"><span data-stu-id="c457a-168">The order of a composite transformation is important.</span></span> <span data-ttu-id="c457a-169">一般情況下，旋轉，然後調整，然後轉換並不相同小數位數為然後旋轉，然後轉換。</span><span class="sxs-lookup"><span data-stu-id="c457a-169">In general, rotate, then scale, then translate is not the same as scale, then rotate, then translate.</span></span> <span data-ttu-id="c457a-170">同樣地，矩陣相乘的順序很重要的。</span><span class="sxs-lookup"><span data-stu-id="c457a-170">Similarly, the order of matrix multiplication is important.</span></span> <span data-ttu-id="c457a-171">一般情況下，ABC 不與備份相同。</span><span class="sxs-lookup"><span data-stu-id="c457a-171">In general, ABC is not the same as BAC.</span></span>  
  
 <span data-ttu-id="c457a-172"><xref:System.Drawing.Drawing2D.Matrix>類別提供多種方法來建置複合轉換： <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>， <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>， <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>， <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>， <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>，和<xref:System.Drawing.Drawing2D.Matrix.Translate%2A>。</span><span class="sxs-lookup"><span data-stu-id="c457a-172">The <xref:System.Drawing.Drawing2D.Matrix> class provides several methods for building a composite transformation: <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>, <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>, <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>, <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>, <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>, and <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>.</span></span> <span data-ttu-id="c457a-173">下列範例會建立複合的轉換，先旋轉 30 度，則在 y 方向的 2 倍縮放，然後再平移 x 方向的 5 個單位矩陣：</span><span class="sxs-lookup"><span data-stu-id="c457a-173">The following example creates the matrix of a composite transformation that first rotates 30 degrees, then scales by a factor of 2 in the y direction, and then translates 5 units in the x direction:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 <span data-ttu-id="c457a-174">下圖顯示矩陣。</span><span class="sxs-lookup"><span data-stu-id="c457a-174">The following illustration shows the matrix.</span></span>  
  
 <span data-ttu-id="c457a-175">![Transformations](./media/aboutgdip05-art13.gif "AboutGdip05_art13")</span><span class="sxs-lookup"><span data-stu-id="c457a-175">![Transformations](./media/aboutgdip05-art13.gif "AboutGdip05_art13")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c457a-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c457a-176">See also</span></span>

- [<span data-ttu-id="c457a-177">座標系統和轉換</span><span class="sxs-lookup"><span data-stu-id="c457a-177">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
- [<span data-ttu-id="c457a-178">使用 Managed GDI+ 中的轉換</span><span class="sxs-lookup"><span data-stu-id="c457a-178">Using Transformations in Managed GDI+</span></span>](using-transformations-in-managed-gdi.md)
