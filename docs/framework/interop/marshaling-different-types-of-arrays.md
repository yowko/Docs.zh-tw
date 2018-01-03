---
title: "封送處理不同類型的陣列"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e34a0b267e9a1dc7cf545ae981211cabf220e0d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="64a14-102">封送處理不同類型的陣列</span><span class="sxs-lookup"><span data-stu-id="64a14-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="64a14-103">陣列是 Managed 程式碼中的參考類型，它包含一或多個相同類型的項目。</span><span class="sxs-lookup"><span data-stu-id="64a14-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="64a14-104">雖然陣列是參考類型，它們會做為 In 參數傳遞至 Unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="64a14-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="64a14-105">此行為與 Managed 陣列傳遞至 Managed 物件的方式 (做為 In/Out 參數) 不一致。</span><span class="sxs-lookup"><span data-stu-id="64a14-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="64a14-106">如需詳細資訊，請參閱 [複製和固定](../../../docs/framework/interop/copying-and-pinning.md)。</span><span class="sxs-lookup"><span data-stu-id="64a14-106">For additional details, see [Copying and Pinning](../../../docs/framework/interop/copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="64a14-107">下表列出陣列的封送處理選項，並說明其用法。</span><span class="sxs-lookup"><span data-stu-id="64a14-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="64a14-108">陣列</span><span class="sxs-lookup"><span data-stu-id="64a14-108">Array</span></span>|<span data-ttu-id="64a14-109">描述</span><span class="sxs-lookup"><span data-stu-id="64a14-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="64a14-110">傳值方式的整數。</span><span class="sxs-lookup"><span data-stu-id="64a14-110">Of integers by value.</span></span>|<span data-ttu-id="64a14-111">將整數的陣列做為 In 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="64a14-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="64a14-112">傳址方式的整數。</span><span class="sxs-lookup"><span data-stu-id="64a14-112">Of integers by reference.</span></span>|<span data-ttu-id="64a14-113">將整數的陣列做為 In/Out 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="64a14-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="64a14-114">傳值方式的整數 (二維)。</span><span class="sxs-lookup"><span data-stu-id="64a14-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="64a14-115">將整數的矩陣做為 In 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="64a14-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="64a14-116">傳值方式的字串。</span><span class="sxs-lookup"><span data-stu-id="64a14-116">Of strings by value.</span></span>|<span data-ttu-id="64a14-117">將字串的陣列做為 In 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="64a14-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="64a14-118">整數的結構。</span><span class="sxs-lookup"><span data-stu-id="64a14-118">Of structures with integers.</span></span>|<span data-ttu-id="64a14-119">將包含整數的結構陣列做為 In/Out 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="64a14-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="64a14-120">字串的結構。</span><span class="sxs-lookup"><span data-stu-id="64a14-120">Of structures with strings.</span></span>|<span data-ttu-id="64a14-121">將僅包含整數的結構陣列做為 In/Out 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="64a14-121">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="64a14-122">可變更陣列的成員。</span><span class="sxs-lookup"><span data-stu-id="64a14-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="64a14-123">範例</span><span class="sxs-lookup"><span data-stu-id="64a14-123">Example</span></span>  
 <span data-ttu-id="64a14-124">本範例示範如何傳遞下列類型的陣列：</span><span class="sxs-lookup"><span data-stu-id="64a14-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
-   <span data-ttu-id="64a14-125">傳值方式的整數陣列。</span><span class="sxs-lookup"><span data-stu-id="64a14-125">Array of integers by value.</span></span>  
  
-   <span data-ttu-id="64a14-126">傳址方式的整數陣列，可調整大小。</span><span class="sxs-lookup"><span data-stu-id="64a14-126">Array of integers by reference, which can be resized.</span></span>  
  
-   <span data-ttu-id="64a14-127">傳值方式的整數多維度陣列 (矩陣)。</span><span class="sxs-lookup"><span data-stu-id="64a14-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
-   <span data-ttu-id="64a14-128">傳值方式的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="64a14-128">Array of strings by value.</span></span>  
  
-   <span data-ttu-id="64a14-129">整數的結構陣列。</span><span class="sxs-lookup"><span data-stu-id="64a14-129">Array of structures with integers.</span></span>  
  
-   <span data-ttu-id="64a14-130">字串的結構陣列。</span><span class="sxs-lookup"><span data-stu-id="64a14-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="64a14-131">除非陣列是明確地以傳值方式封送處理，否則預設行為會將陣列封送處理做為 In 參數。</span><span class="sxs-lookup"><span data-stu-id="64a14-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="64a14-132">您可以明確套用 <xref:System.Runtime.InteropServices.InAttribute> 和 <xref:System.Runtime.InteropServices.OutAttribute> 屬性來變更此行為。</span><span class="sxs-lookup"><span data-stu-id="64a14-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="64a14-133">陣列範例會使用下列 Unmanaged 函式，和其原始函式宣告：</span><span class="sxs-lookup"><span data-stu-id="64a14-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="64a14-134">從 PinvokeLib.dll 匯出的**TestArrayOfInts** 。</span><span class="sxs-lookup"><span data-stu-id="64a14-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
-   <span data-ttu-id="64a14-135">從 PinvokeLib.dll 匯出的**TestRefArrayOfInts** 。</span><span class="sxs-lookup"><span data-stu-id="64a14-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
-   <span data-ttu-id="64a14-136">從 PinvokeLib.dll 匯出的**TestMatrixOfInts** 。</span><span class="sxs-lookup"><span data-stu-id="64a14-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
-   <span data-ttu-id="64a14-137">從 PinvokeLib.dll 匯出的**TestArrayOfStrings** 。</span><span class="sxs-lookup"><span data-stu-id="64a14-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
-   <span data-ttu-id="64a14-138">從 PinvokeLib.dll 匯出的**TestArrayOfStructs** 。</span><span class="sxs-lookup"><span data-stu-id="64a14-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
-   <span data-ttu-id="64a14-139">從 PinvokeLib.dll 匯出的**TestArrayOfStructs2** 。</span><span class="sxs-lookup"><span data-stu-id="64a14-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="64a14-140">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) 是自訂的 Unmanaged 程式庫，包含先前所列出函式和 2 個結構變數的實作： **MYPOINT** 和 **MYPERSON**。</span><span class="sxs-lookup"><span data-stu-id="64a14-140">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="64a14-141">這些結構包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="64a14-141">The structures contain the following elements:</span></span>  
  
```  
typedef struct _MYPOINT  
{  
   int x;   
   int y;   
} MYPOINT;  
  
typedef struct _MYPERSON  
{  
   char* first;   
   char* last;   
} MYPERSON;  
```  
  
 <span data-ttu-id="64a14-142">在此範例中，`MyPoint` 和 `MyPerson` 結構包含內嵌類型。</span><span class="sxs-lookup"><span data-stu-id="64a14-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="64a14-143">已設定 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性來確定此成員以其顯示的順序循序排列在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="64a14-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="64a14-144">`LibWrap` 類別包含一組 `App` 類別所呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="64a14-144">The `LibWrap` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="64a14-145">如需傳遞陣列的特定詳細資訊，請參閱下面範例中的註解。</span><span class="sxs-lookup"><span data-stu-id="64a14-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="64a14-146">陣列是參考類型，它預設是做為 In 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="64a14-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="64a14-147">呼叫端若要接收結果， **InAttribute** 和 **OutAttribute** 必須明確地套用至包含陣列的引數。</span><span class="sxs-lookup"><span data-stu-id="64a14-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="64a14-148">宣告原型</span><span class="sxs-lookup"><span data-stu-id="64a14-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="64a14-149">呼叫函式</span><span class="sxs-lookup"><span data-stu-id="64a14-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="64a14-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="64a14-150">See Also</span></span>  
 [<span data-ttu-id="64a14-151">封送處理類型的陣列</span><span class="sxs-lookup"><span data-stu-id="64a14-151">Marshaling Arrays of Types</span></span>](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)  
 [<span data-ttu-id="64a14-152">平台叫用資料類型</span><span class="sxs-lookup"><span data-stu-id="64a14-152">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="64a14-153">在 Managed 程式碼中建立原型</span><span class="sxs-lookup"><span data-stu-id="64a14-153">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
