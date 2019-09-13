---
title: 封送處理不同類型的陣列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 358c7f1a339fd473271574a4e97e201f5c15f871
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894175"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="43b6c-102">封送處理不同類型的陣列</span><span class="sxs-lookup"><span data-stu-id="43b6c-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="43b6c-103">陣列是 Managed 程式碼中的參考類型，它包含一或多個相同類型的項目。</span><span class="sxs-lookup"><span data-stu-id="43b6c-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="43b6c-104">雖然陣列是參考類型，它們會做為 In 參數傳遞至 Unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="43b6c-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="43b6c-105">此行為與 Managed 陣列傳遞至 Managed 物件的方式 (做為 In/Out 參數) 不一致。</span><span class="sxs-lookup"><span data-stu-id="43b6c-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="43b6c-106">如需詳細資訊，請參閱 [複製和固定](copying-and-pinning.md)。</span><span class="sxs-lookup"><span data-stu-id="43b6c-106">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="43b6c-107">下表列出陣列的封送處理選項，並說明其用法。</span><span class="sxs-lookup"><span data-stu-id="43b6c-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="43b6c-108">陣列</span><span class="sxs-lookup"><span data-stu-id="43b6c-108">Array</span></span>|<span data-ttu-id="43b6c-109">描述</span><span class="sxs-lookup"><span data-stu-id="43b6c-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="43b6c-110">傳值方式的整數。</span><span class="sxs-lookup"><span data-stu-id="43b6c-110">Of integers by value.</span></span>|<span data-ttu-id="43b6c-111">將整數的陣列做為 In 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="43b6c-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="43b6c-112">傳址方式的整數。</span><span class="sxs-lookup"><span data-stu-id="43b6c-112">Of integers by reference.</span></span>|<span data-ttu-id="43b6c-113">將整數的陣列做為 In/Out 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="43b6c-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="43b6c-114">傳值方式的整數 (二維)。</span><span class="sxs-lookup"><span data-stu-id="43b6c-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="43b6c-115">將整數的矩陣做為 In 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="43b6c-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="43b6c-116">傳值方式的字串。</span><span class="sxs-lookup"><span data-stu-id="43b6c-116">Of strings by value.</span></span>|<span data-ttu-id="43b6c-117">將字串的陣列做為 In 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="43b6c-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="43b6c-118">整數的結構。</span><span class="sxs-lookup"><span data-stu-id="43b6c-118">Of structures with integers.</span></span>|<span data-ttu-id="43b6c-119">將包含整數的結構陣列做為 In/Out 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="43b6c-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="43b6c-120">字串的結構。</span><span class="sxs-lookup"><span data-stu-id="43b6c-120">Of structures with strings.</span></span>|<span data-ttu-id="43b6c-121">將僅包含字串的結構陣列當作 In/Out 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="43b6c-121">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="43b6c-122">可變更陣列的成員。</span><span class="sxs-lookup"><span data-stu-id="43b6c-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="43b6c-123">範例</span><span class="sxs-lookup"><span data-stu-id="43b6c-123">Example</span></span>  
 <span data-ttu-id="43b6c-124">本範例示範如何傳遞下列類型的陣列：</span><span class="sxs-lookup"><span data-stu-id="43b6c-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
- <span data-ttu-id="43b6c-125">傳值方式的整數陣列。</span><span class="sxs-lookup"><span data-stu-id="43b6c-125">Array of integers by value.</span></span>  
  
- <span data-ttu-id="43b6c-126">傳址方式的整數陣列，可調整大小。</span><span class="sxs-lookup"><span data-stu-id="43b6c-126">Array of integers by reference, which can be resized.</span></span>  
  
- <span data-ttu-id="43b6c-127">傳值方式的整數多維度陣列 (矩陣)。</span><span class="sxs-lookup"><span data-stu-id="43b6c-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
- <span data-ttu-id="43b6c-128">傳值方式的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="43b6c-128">Array of strings by value.</span></span>  
  
- <span data-ttu-id="43b6c-129">整數的結構陣列。</span><span class="sxs-lookup"><span data-stu-id="43b6c-129">Array of structures with integers.</span></span>  
  
- <span data-ttu-id="43b6c-130">字串的結構陣列。</span><span class="sxs-lookup"><span data-stu-id="43b6c-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="43b6c-131">除非陣列是明確地以傳值方式封送處理，否則預設行為會將陣列封送處理做為 In 參數。</span><span class="sxs-lookup"><span data-stu-id="43b6c-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="43b6c-132">您可以明確套用 <xref:System.Runtime.InteropServices.InAttribute> 和 <xref:System.Runtime.InteropServices.OutAttribute> 屬性來變更此行為。</span><span class="sxs-lookup"><span data-stu-id="43b6c-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="43b6c-133">陣列範例會使用下列 Unmanaged 函式，和其原始函式宣告：</span><span class="sxs-lookup"><span data-stu-id="43b6c-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="43b6c-134">從 PinvokeLib.dll 匯出的**TestArrayOfInts** 。</span><span class="sxs-lookup"><span data-stu-id="43b6c-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- <span data-ttu-id="43b6c-135">從 PinvokeLib.dll 匯出的**TestRefArrayOfInts** 。</span><span class="sxs-lookup"><span data-stu-id="43b6c-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- <span data-ttu-id="43b6c-136">從 PinvokeLib.dll 匯出的**TestMatrixOfInts** 。</span><span class="sxs-lookup"><span data-stu-id="43b6c-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- <span data-ttu-id="43b6c-137">從 PinvokeLib.dll 匯出的**TestArrayOfStrings** 。</span><span class="sxs-lookup"><span data-stu-id="43b6c-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- <span data-ttu-id="43b6c-138">從 PinvokeLib.dll 匯出的**TestArrayOfStructs** 。</span><span class="sxs-lookup"><span data-stu-id="43b6c-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- <span data-ttu-id="43b6c-139">從 PinvokeLib.dll 匯出的**TestArrayOfStructs2** 。</span><span class="sxs-lookup"><span data-stu-id="43b6c-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="43b6c-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) 是自訂的 Unmanaged 程式庫，包含先前所列出函式和 2 個結構變數的實作： **MYPOINT** 和 **MYPERSON**。</span><span class="sxs-lookup"><span data-stu-id="43b6c-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="43b6c-141">這些結構包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="43b6c-141">The structures contain the following elements:</span></span>  
  
```cpp
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
  
 <span data-ttu-id="43b6c-142">在此範例中， `MyPoint` 和 `MyPerson` 結構包含內嵌類型。</span><span class="sxs-lookup"><span data-stu-id="43b6c-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="43b6c-143">已設定 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性來確定此成員以其顯示的順序循序排列在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="43b6c-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="43b6c-144">`LibWrap` 類別包含一組 `App` 類別所呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="43b6c-144">The `LibWrap` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="43b6c-145">如需傳遞陣列的特定詳細資訊，請參閱下面範例中的註解。</span><span class="sxs-lookup"><span data-stu-id="43b6c-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="43b6c-146">陣列是參考類型，它預設是做為 In 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="43b6c-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="43b6c-147">呼叫端若要接收結果， **InAttribute** 和 **OutAttribute** 必須明確地套用至包含陣列的引數。</span><span class="sxs-lookup"><span data-stu-id="43b6c-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="43b6c-148">宣告原型</span><span class="sxs-lookup"><span data-stu-id="43b6c-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="43b6c-149">呼叫函式</span><span class="sxs-lookup"><span data-stu-id="43b6c-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="43b6c-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43b6c-150">See also</span></span>

- [<span data-ttu-id="43b6c-151">平台叫用資料類型</span><span class="sxs-lookup"><span data-stu-id="43b6c-151">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="43b6c-152">在 Managed 程式碼中建立原型</span><span class="sxs-lookup"><span data-stu-id="43b6c-152">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
