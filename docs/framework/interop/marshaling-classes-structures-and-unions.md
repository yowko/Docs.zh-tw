---
title: "封送處理類別、結構和等位"
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
- cpp
helpviewer_keywords:
- data marshaling, classes
- marshaling, unions
- marshaling, structures
- marshaling, samples
- data marshaling, structures
- platform invoke, marshaling data
- marshaling, classes
- data marshaling, unions
- data marshaling, samples
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: 027832a2-9b43-4fd9-9b45-7f4196261a4e
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dcfa2e60a9659db6d38e0561785ece5726989ee0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="b264b-102">封送處理類別、結構和等位</span><span class="sxs-lookup"><span data-stu-id="b264b-102">Marshaling Classes, Structures, and Unions</span></span>
<span data-ttu-id="b264b-103">在 .NET Framework 中，類別和結構相類似。</span><span class="sxs-lookup"><span data-stu-id="b264b-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="b264b-104">兩者都可以有欄位、屬性和事件。</span><span class="sxs-lookup"><span data-stu-id="b264b-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="b264b-105">也可以有靜態和非靜態方法。</span><span class="sxs-lookup"><span data-stu-id="b264b-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="b264b-106">一個值得注意的差異在於結構是實值類型，而類別是參考類型。</span><span class="sxs-lookup"><span data-stu-id="b264b-106">One notable difference is that structures are value types and classes are reference types.</span></span>  
  
 <span data-ttu-id="b264b-107">下表列出類別、結構和等位的封送處理選項，並描述其用法，以及提供對應平台的叫用範例連結。</span><span class="sxs-lookup"><span data-stu-id="b264b-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>  
  
|<span data-ttu-id="b264b-108">類型</span><span class="sxs-lookup"><span data-stu-id="b264b-108">Type</span></span>|<span data-ttu-id="b264b-109">描述</span><span class="sxs-lookup"><span data-stu-id="b264b-109">Description</span></span>|<span data-ttu-id="b264b-110">範例</span><span class="sxs-lookup"><span data-stu-id="b264b-110">Sample</span></span>|  
|----------|-----------------|------------|  
|<span data-ttu-id="b264b-111">傳值呼叫</span><span class="sxs-lookup"><span data-stu-id="b264b-111">Class by value.</span></span>|<span data-ttu-id="b264b-112">做為 In/Out 參數，如 Managed 案例，會傳遞具有整數成員的類別。</span><span class="sxs-lookup"><span data-stu-id="b264b-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|<span data-ttu-id="b264b-113">SysTime 範例</span><span class="sxs-lookup"><span data-stu-id="b264b-113">SysTime sample</span></span>|  
|<span data-ttu-id="b264b-114">結構傳值。</span><span class="sxs-lookup"><span data-stu-id="b264b-114">Structure by value.</span></span>|<span data-ttu-id="b264b-115">傳遞結構做為 In 參數。</span><span class="sxs-lookup"><span data-stu-id="b264b-115">Passes structures as In parameters.</span></span>|<span data-ttu-id="b264b-116">結構範例</span><span class="sxs-lookup"><span data-stu-id="b264b-116">Structures sample</span></span>|  
|<span data-ttu-id="b264b-117">結構傳址。</span><span class="sxs-lookup"><span data-stu-id="b264b-117">Structure by reference.</span></span>|<span data-ttu-id="b264b-118">傳遞結構做為 In/Out 參數。</span><span class="sxs-lookup"><span data-stu-id="b264b-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="b264b-119">OSInfo 範例</span><span class="sxs-lookup"><span data-stu-id="b264b-119">OSInfo sample</span></span>|  
|<span data-ttu-id="b264b-120">具有巢狀結構 (扁平化) 的結構。</span><span class="sxs-lookup"><span data-stu-id="b264b-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="b264b-121">傳遞類別，表示具有 Unmanaged 函式中巢狀結構的結構。</span><span class="sxs-lookup"><span data-stu-id="b264b-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="b264b-122">在 Managed 原型中，結構被扁平化為一個大的結構。</span><span class="sxs-lookup"><span data-stu-id="b264b-122">The structure is flattened to one big structure in the managed prototype.</span></span>|<span data-ttu-id="b264b-123">FindFile 範例</span><span class="sxs-lookup"><span data-stu-id="b264b-123">FindFile sample</span></span>|  
|<span data-ttu-id="b264b-124">指標指向另一個結構的結構。</span><span class="sxs-lookup"><span data-stu-id="b264b-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="b264b-125">傳遞一個結構，其包含的指標指向第二個做為成員的結構。</span><span class="sxs-lookup"><span data-stu-id="b264b-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|<span data-ttu-id="b264b-126">結構範例</span><span class="sxs-lookup"><span data-stu-id="b264b-126">Structures Sample</span></span>|  
|<span data-ttu-id="b264b-127">整數傳值的結構陣列。</span><span class="sxs-lookup"><span data-stu-id="b264b-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="b264b-128">傳遞僅包含整數做為 In/Out 參數的結構陣列。</span><span class="sxs-lookup"><span data-stu-id="b264b-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="b264b-129">可變更陣列的成員。</span><span class="sxs-lookup"><span data-stu-id="b264b-129">Members of the array can be changed.</span></span>|<span data-ttu-id="b264b-130">陣列範例</span><span class="sxs-lookup"><span data-stu-id="b264b-130">Arrays Sample</span></span>|  
|<span data-ttu-id="b264b-131">整數結構和傳址字串的陣列。</span><span class="sxs-lookup"><span data-stu-id="b264b-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="b264b-132">傳遞包含整數和字串做為 Out 參數的結構陣列。</span><span class="sxs-lookup"><span data-stu-id="b264b-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="b264b-133">所呼叫的函式會配置此陣列的記憶體。</span><span class="sxs-lookup"><span data-stu-id="b264b-133">The called function allocates memory for the array.</span></span>|<span data-ttu-id="b264b-134">OutArrayOfStructs 範例</span><span class="sxs-lookup"><span data-stu-id="b264b-134">OutArrayOfStructs Sample</span></span>|  
|<span data-ttu-id="b264b-135">具有實值類型的等位。</span><span class="sxs-lookup"><span data-stu-id="b264b-135">Unions with value types.</span></span>|<span data-ttu-id="b264b-136">傳遞具有實值類型的等位 (整數和雙精度浮點數)。</span><span class="sxs-lookup"><span data-stu-id="b264b-136">Passes unions with value types (integer and double).</span></span>|<span data-ttu-id="b264b-137">等位範例</span><span class="sxs-lookup"><span data-stu-id="b264b-137">Unions sample</span></span>|  
|<span data-ttu-id="b264b-138">具有混合類型的等位。</span><span class="sxs-lookup"><span data-stu-id="b264b-138">Unions with mixed types.</span></span>|<span data-ttu-id="b264b-139">傳遞具有混合類型的等位 (整數和字串)。</span><span class="sxs-lookup"><span data-stu-id="b264b-139">Passes unions with mixed types (integer and string).</span></span>|<span data-ttu-id="b264b-140">等位範例</span><span class="sxs-lookup"><span data-stu-id="b264b-140">Unions sample</span></span>|  
|<span data-ttu-id="b264b-141">在結構中的 null 值。</span><span class="sxs-lookup"><span data-stu-id="b264b-141">Null values in structure.</span></span>|<span data-ttu-id="b264b-142">傳遞 Null 參考 (在 Visual Basic 中為 **Nothing**)，而非實值型別的參考。</span><span class="sxs-lookup"><span data-stu-id="b264b-142">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="b264b-143">HandleRef 範例</span><span class="sxs-lookup"><span data-stu-id="b264b-143">HandleRef sample</span></span>|  
  
## <a name="structures-sample"></a><span data-ttu-id="b264b-144">結構範例</span><span class="sxs-lookup"><span data-stu-id="b264b-144">Structures sample</span></span>  
 <span data-ttu-id="b264b-145">這個範例示範如何傳遞指向第二個結構的結構、傳遞具有內嵌結構的結構，以及傳遞具有內嵌陣列的結構。</span><span class="sxs-lookup"><span data-stu-id="b264b-145">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
 <span data-ttu-id="b264b-146">本結構範例會使用下列 Unmanaged 函式，和其原始函式宣告，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b264b-146">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="b264b-147">從 PinvokeLib.dll 匯出的 **TestStructInStruct**。</span><span class="sxs-lookup"><span data-stu-id="b264b-147">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
-   <span data-ttu-id="b264b-148">從 PinvokeLib.dll 匯出的 **TestStructInStruct3**。</span><span class="sxs-lookup"><span data-stu-id="b264b-148">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
-   <span data-ttu-id="b264b-149">從 PinvokeLib.dll 匯出的 **TestArrayInStruct**。</span><span class="sxs-lookup"><span data-stu-id="b264b-149">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 <span data-ttu-id="b264b-150">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) 是自訂的 Unmanaged 程式庫，其中包含先前所列出函式和四個結構的實作：**MYPERSON**、**MYPERSON2**、**MYPERSON3** 和 **MYARRAYSTRUCT**。</span><span class="sxs-lookup"><span data-stu-id="b264b-150">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="b264b-151">這些結構包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="b264b-151">These structures contain the following elements:</span></span>  
  
```  
typedef struct _MYPERSON  
{  
   char* first;   
   char* last;   
} MYPERSON, *LP_MYPERSON;  
  
typedef struct _MYPERSON2  
{  
   MYPERSON* person;  
   int age;   
} MYPERSON2, *LP_MYPERSON2;  
  
typedef struct _MYPERSON3  
{  
   MYPERSON person;  
   int age;   
} MYPERSON3;  
  
typedef struct _MYARRAYSTRUCT  
{  
   bool flag;  
   int vals[ 3 ];   
} MYARRAYSTRUCT;  
```  
  
 <span data-ttu-id="b264b-152">Managed `MyPerson`、`MyPerson2`、`MyPerson3` 和 `MyArrayStruct` 結構的特性如下：</span><span class="sxs-lookup"><span data-stu-id="b264b-152">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>  
  
-   <span data-ttu-id="b264b-153">`MyPerson` 僅包含字串成員。</span><span class="sxs-lookup"><span data-stu-id="b264b-153">`MyPerson` contains only string members.</span></span> <span data-ttu-id="b264b-154">當傳遞給 Unmanaged 函式時，[CharSet](../../../docs/framework/interop/specifying-a-character-set.md) 欄位會將字串設定為 ANSI 格式。</span><span class="sxs-lookup"><span data-stu-id="b264b-154">The [CharSet](../../../docs/framework/interop/specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>  
  
-   <span data-ttu-id="b264b-155">`MyPerson2` 包含 `MyPerson` 結構的 **IntPtr**。</span><span class="sxs-lookup"><span data-stu-id="b264b-155">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="b264b-156">**IntPtr** 類型會取代原始指標的 Unmanaged 結構，因為 .NET Framework 應用程式不會使用指標，除非將程式碼標示為 **Unsafe**。</span><span class="sxs-lookup"><span data-stu-id="b264b-156">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>  
  
-   <span data-ttu-id="b264b-157">`MyPerson3` 包含 `MyPerson` 做為內嵌結構。</span><span class="sxs-lookup"><span data-stu-id="b264b-157">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="b264b-158">藉由將內嵌結構的項目放在主結構中，可扁平化內嵌於其它結構的結構，或者將它留下做為內嵌結構，如本範例所完成的動作。</span><span class="sxs-lookup"><span data-stu-id="b264b-158">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>  
  
-   <span data-ttu-id="b264b-159">`MyArrayStruct` 包含一個整數的陣列。</span><span class="sxs-lookup"><span data-stu-id="b264b-159">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="b264b-160"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性會將 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉值設定為 **ByValArray**，用來表示陣列項目數。</span><span class="sxs-lookup"><span data-stu-id="b264b-160">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>  
  
 <span data-ttu-id="b264b-161">對於本範例的所有結構，套用 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性來確定此成員以其顯示的順序循序排列在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="b264b-161">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="b264b-162">`LibWrap` 類別包含 `TestStructInStruct`、`TestStructInStruct3` 及 `TestArrayInStruct` 方法的 Managed 原型，這些方法由 `App` 類別所呼叫。</span><span class="sxs-lookup"><span data-stu-id="b264b-162">The `LibWrap` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="b264b-163">每一個原型會宣告單一參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b264b-163">Each prototype declares a single parameter, as follows:</span></span>  
  
-   <span data-ttu-id="b264b-164">`TestStructInStruct` 宣告一個參考給 `MyPerson2` 類型做為它的參數。</span><span class="sxs-lookup"><span data-stu-id="b264b-164">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>  
  
-   <span data-ttu-id="b264b-165">`TestStructInStruct3` 宣告 `MyPerson3` 類型做為它的參數，並以傳值方式傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="b264b-165">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>  
  
-   <span data-ttu-id="b264b-166">`TestArrayInStruct` 宣告一個參考給 `MyArrayStruct` 類型做為它的參數。</span><span class="sxs-lookup"><span data-stu-id="b264b-166">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>  
  
 <span data-ttu-id="b264b-167">除非此參數包含 **ref** 關鍵字 (在 Visual Basic 中為 **ByRef**)，否則作為方法引數的結構會以傳值方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="b264b-167">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="b264b-168">例如， `TestStructInStruct` 方法會傳遞對於類型物件 `MyPerson2` 的參考 (位址的值) 給 Unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b264b-168">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="b264b-169">若要管理 `MyPerson2` 指向的結構，此範例會建立指定大小的緩衝區，並藉由合併 <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> 和 <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> 方法，傳回其位址。</span><span class="sxs-lookup"><span data-stu-id="b264b-169">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="b264b-170">接下來，範例會將 Managed 結構的內容複製到 Unmanaged 緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b264b-170">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="b264b-171">最後，此範例會使用 <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> 方法自 Unmanaged 緩衝區封送處理資料到 Managed 物件，並以 <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> 方法來釋放 Unmanaged 記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="b264b-171">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="b264b-172">宣告原型</span><span class="sxs-lookup"><span data-stu-id="b264b-172">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a><span data-ttu-id="b264b-173">呼叫函式</span><span class="sxs-lookup"><span data-stu-id="b264b-173">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a><span data-ttu-id="b264b-174">FindFile 範例</span><span class="sxs-lookup"><span data-stu-id="b264b-174">FindFile sample</span></span>  
 <span data-ttu-id="b264b-175">這個範例示範如何傳遞包含第二個內嵌結構的結構給 Unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="b264b-175">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="b264b-176">它也會示範如何使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性在結構內宣告固定長度的陣列。</span><span class="sxs-lookup"><span data-stu-id="b264b-176">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="b264b-177">在此範例中，會加入內嵌結構項目至其父結構。</span><span class="sxs-lookup"><span data-stu-id="b264b-177">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="b264b-178">如需未扁平化內嵌結構的範例，請參閱[結構範例](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e)。</span><span class="sxs-lookup"><span data-stu-id="b264b-178">For a sample of an embedded structure that is not flattened, see [Structures Sample](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e).</span></span>  
  
 <span data-ttu-id="b264b-179">FindFile 範例會使用下列 Unmanaged 函式，和其原始函式宣告，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b264b-179">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="b264b-180">從 Kernel32.dll 匯出 **FindFirstFile**。</span><span class="sxs-lookup"><span data-stu-id="b264b-180">**FindFirstFile** exported from Kernel32.dll.</span></span>  
  
    ```  
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 <span data-ttu-id="b264b-181">傳遞至函式的原始結構包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="b264b-181">The original structure passed to the function contains the following elements:</span></span>  
  
```  
typedef struct _WIN32_FIND_DATA   
{  
  DWORD    dwFileAttributes;   
  FILETIME ftCreationTime;   
  FILETIME ftLastAccessTime;   
  FILETIME ftLastWriteTime;   
  DWORD    nFileSizeHigh;   
  DWORD    nFileSizeLow;   
  DWORD    dwReserved0;   
  DWORD    dwReserved1;   
  TCHAR    cFileName[ MAX_PATH ];   
  TCHAR    cAlternateFileName[ 14 ];   
} WIN32_FIND_DATA, *PWIN32_FIND_DATA;  
```  
  
 <span data-ttu-id="b264b-182">在此範例中， `FindData` 類別包含原始結構的每個項目所對應的資料成員和內嵌結構。</span><span class="sxs-lookup"><span data-stu-id="b264b-182">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="b264b-183">為了取代 2 個原始字元緩衝區，類別會替代字串。</span><span class="sxs-lookup"><span data-stu-id="b264b-183">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="b264b-184">**MarshalAsAttribute** 會將 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉設定為 **ByValTStr**，這用來識別出現在 Unmanaged 結構中內嵌固定長度的字元陣列。</span><span class="sxs-lookup"><span data-stu-id="b264b-184">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>  
  
 <span data-ttu-id="b264b-185">`LibWrap` 類別包含 `FindFirstFile` 方法的 Managed 原型，會傳遞 `FindData` 類別做為參數。</span><span class="sxs-lookup"><span data-stu-id="b264b-185">The `LibWrap` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="b264b-186">參數必須以 <xref:System.Runtime.InteropServices.InAttribute> 和 <xref:System.Runtime.InteropServices.OutAttribute> 屬性宣告，因為根據預設，會傳遞參考類型的類別做為 In 參數。</span><span class="sxs-lookup"><span data-stu-id="b264b-186">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="b264b-187">宣告原型</span><span class="sxs-lookup"><span data-stu-id="b264b-187">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a><span data-ttu-id="b264b-188">呼叫函式</span><span class="sxs-lookup"><span data-stu-id="b264b-188">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a><span data-ttu-id="b264b-189">等位範例</span><span class="sxs-lookup"><span data-stu-id="b264b-189">Unions sample</span></span>  
 <span data-ttu-id="b264b-190">這個範例示範如何傳遞結構至需要等位的 Unmanged 函式，該結構僅包含實值類型、包含實值類型的結構和一個做為參數的字串。</span><span class="sxs-lookup"><span data-stu-id="b264b-190">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="b264b-191">等位表示可由兩個或多個變數共用的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="b264b-191">A union represents a memory location that can be shared by two or more variables.</span></span>  
  
 <span data-ttu-id="b264b-192">Unions 範例會使用下列 Unmanaged 函式，和其原始函式宣告，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b264b-192">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="b264b-193">從 PinvokeLib.dll 匯出的 **TestUnion**。</span><span class="sxs-lookup"><span data-stu-id="b264b-193">**TestUnion** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestUnion(MYUNION u, int type);  
    ```  
  
 <span data-ttu-id="b264b-194">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) 是自訂的 Unmanaged 程式庫，其中包含先前所列出函式以及 **MYUNION** 和 **MYUNION2** 這兩個等位的實作。</span><span class="sxs-lookup"><span data-stu-id="b264b-194">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="b264b-195">此等位包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="b264b-195">The unions contain the following elements:</span></span>  
  
```  
union MYUNION  
{  
    int number;  
    double d;  
}  
  
union MYUNION2  
{  
    int i;  
    char str[128];  
};  
```  
  
 <span data-ttu-id="b264b-196">在 Managed 程式碼中，會定義等位為結構。</span><span class="sxs-lookup"><span data-stu-id="b264b-196">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="b264b-197">`MyUnion` 結構包含兩個做為其成員的實值類型：整數和雙精度浮點數。</span><span class="sxs-lookup"><span data-stu-id="b264b-197">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="b264b-198">設定 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性來控制每個資料成員的精確位置。</span><span class="sxs-lookup"><span data-stu-id="b264b-198">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="b264b-199"><xref:System.Runtime.InteropServices.FieldOffsetAttribute> 屬性會提供等位的 Unmanaged 表示中的欄位實體位置。</span><span class="sxs-lookup"><span data-stu-id="b264b-199">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="b264b-200">請注意這兩個成員具有相同的位移值，所以成員可以定義相同的記憶體。</span><span class="sxs-lookup"><span data-stu-id="b264b-200">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>  
  
 <span data-ttu-id="b264b-201">`MyUnion2_1` 和 `MyUnion2_2` 分別包含實值類型 (整數) 和字串。</span><span class="sxs-lookup"><span data-stu-id="b264b-201">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="b264b-202">在 Managed 程式碼中，實值類型及參考類型不允許重疊。</span><span class="sxs-lookup"><span data-stu-id="b264b-202">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="b264b-203">此範例會使用方法多載化來讓呼叫端在呼叫相同 Unmanaged 函式時使用這兩種類型。</span><span class="sxs-lookup"><span data-stu-id="b264b-203">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="b264b-204">`MyUnion2_1` 配置則是明確的，且具有精確位移值。</span><span class="sxs-lookup"><span data-stu-id="b264b-204">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="b264b-205">相反地，`MyUnion2_2` 具有循序配置，因為對參考類型不允許明確的配置。</span><span class="sxs-lookup"><span data-stu-id="b264b-205">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="b264b-206"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性會將 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉設定為 **ByValTStr**，這用來識別出現在該等位的 Unmanaged 表示中內嵌固定長度的字元陣列。</span><span class="sxs-lookup"><span data-stu-id="b264b-206">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>  
  
 <span data-ttu-id="b264b-207">`LibWrap` 類別包含 `TestUnion` 和 `TestUnion2` 方法的原型。</span><span class="sxs-lookup"><span data-stu-id="b264b-207">The `LibWrap` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="b264b-208">`TestUnion2` 被多載，以宣告 `MyUnion2_1` 或 `MyUnion2_2` 做為參數。</span><span class="sxs-lookup"><span data-stu-id="b264b-208">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="b264b-209">宣告原型</span><span class="sxs-lookup"><span data-stu-id="b264b-209">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a><span data-ttu-id="b264b-210">呼叫函式</span><span class="sxs-lookup"><span data-stu-id="b264b-210">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a><span data-ttu-id="b264b-211">SysTime 範例</span><span class="sxs-lookup"><span data-stu-id="b264b-211">SysTime sample</span></span>  
 <span data-ttu-id="b264b-212">這個範例示範如何將指向類別的指標傳遞至需要指向結構指標的 Unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="b264b-212">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>  
  
 <span data-ttu-id="b264b-213">SysTime 範例會使用下列 Unmanaged 函式，和其原始函式宣告，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b264b-213">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="b264b-214">從 Kernel32.dll 匯出 **GetSystemTime**。</span><span class="sxs-lookup"><span data-stu-id="b264b-214">**GetSystemTime** exported from Kernel32.dll.</span></span>  
  
    ```  
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 <span data-ttu-id="b264b-215">傳遞至函式的原始結構包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="b264b-215">The original structure passed to the function contains the following elements:</span></span>  
  
```  
typedef struct _SYSTEMTIME {   
    WORD wYear;   
    WORD wMonth;   
    WORD wDayOfWeek;   
    WORD wDay;   
    WORD wHour;   
    WORD wMinute;   
    WORD wSecond;   
    WORD wMilliseconds;   
} SYSTEMTIME, *PSYSTEMTIME;  
```  
  
 <span data-ttu-id="b264b-216">在此範例中，`SystemTime` 類別包含表示為類別成員原始結構的項目。</span><span class="sxs-lookup"><span data-stu-id="b264b-216">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="b264b-217">設定 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性來確定此成員以其顯示的順序循序排列在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="b264b-217">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="b264b-218">`LibWrap` 類別包含 `GetSystemTime` 方法的 Managed 原型，根據預設會傳遞 `SystemTime` 類別做為 In/Out 參數。</span><span class="sxs-lookup"><span data-stu-id="b264b-218">The `LibWrap` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="b264b-219">參數必須以 <xref:System.Runtime.InteropServices.InAttribute> 和 <xref:System.Runtime.InteropServices.OutAttribute> 屬性宣告，因為根據預設，會傳遞參考類型的類別做為 In 參數。</span><span class="sxs-lookup"><span data-stu-id="b264b-219">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="b264b-220">若要讓呼叫端接收結果，則必須明確地套用這些[方向屬性](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2)。</span><span class="sxs-lookup"><span data-stu-id="b264b-220">For the caller to receive the results, these [directional attributes](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2) must be applied explicitly.</span></span> <span data-ttu-id="b264b-221">`App` 類別建立 `SystemTime` 類別的新執行個體，並存取其資料欄位。</span><span class="sxs-lookup"><span data-stu-id="b264b-221">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>  
  
### <a name="code-samples"></a><span data-ttu-id="b264b-222">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="b264b-222">Code Samples</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a><span data-ttu-id="b264b-223">OutArrayOfStructs 範例</span><span class="sxs-lookup"><span data-stu-id="b264b-223">OutArrayOfStructs sample</span></span>  
 <span data-ttu-id="b264b-224">這個範例顯示如何傳遞包含整數和字串做為 Out 參數的結構陣列至 Unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="b264b-224">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>  
  
 <span data-ttu-id="b264b-225">這個範例示範如何藉由使用 <xref:System.Runtime.InteropServices.Marshal> 類別和使用 Unsafe 程式碼來呼叫原生函式。</span><span class="sxs-lookup"><span data-stu-id="b264b-225">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>  
  
 <span data-ttu-id="b264b-226">這個範例使用定義在 [PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) 中的包裝函式和平台叫用，這些也在原始程式檔中提供。</span><span class="sxs-lookup"><span data-stu-id="b264b-226">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614), also provided in the source files.</span></span> <span data-ttu-id="b264b-227">它會使用 `TestOutArrayOfStructs` 函式和 `MYSTRSTRUCT2` 結構。</span><span class="sxs-lookup"><span data-stu-id="b264b-227">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="b264b-228">此結構包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="b264b-228">The structure contains the following elements:</span></span>  
  
```  
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 <span data-ttu-id="b264b-229">`MyStruct` 類別包含 ANSI 字元的字串物件。</span><span class="sxs-lookup"><span data-stu-id="b264b-229">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="b264b-230"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> 欄位指定 ANSI 格式。</span><span class="sxs-lookup"><span data-stu-id="b264b-230">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="b264b-231">`MyUnsafeStruct` 為包含 <xref:System.IntPtr> 類型的結構，而非字串。</span><span class="sxs-lookup"><span data-stu-id="b264b-231">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>  
  
 <span data-ttu-id="b264b-232">`LibWrap` 類別包含 `TestOutArrayOfStructs` 多載原型方法。</span><span class="sxs-lookup"><span data-stu-id="b264b-232">The `LibWrap` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="b264b-233">如果方法宣告指標做為參數，此類別會以 `unsafe` 關鍵字標記。</span><span class="sxs-lookup"><span data-stu-id="b264b-233">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="b264b-234">因為 [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] 不能使用 Unsafe 程式碼，所以多載的方法、Unsafe 修飾詞和 `MyUnsafeStruct` 結構是不必要的。</span><span class="sxs-lookup"><span data-stu-id="b264b-234">Because [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>  
  
 <span data-ttu-id="b264b-235">`App` 類別會實作 `UsingMarshaling` 方法，該方法會執行所有用來傳遞陣列的必要工作。</span><span class="sxs-lookup"><span data-stu-id="b264b-235">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="b264b-236">該陣列以 `out` (在 Visual Basic 中為`ByRef`) 關鍵字標記，表示該資料從被呼叫端傳遞至呼叫端。</span><span class="sxs-lookup"><span data-stu-id="b264b-236">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="b264b-237">此實作會使用下列 <xref:System.Runtime.InteropServices.Marshal> 類別方法：</span><span class="sxs-lookup"><span data-stu-id="b264b-237">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>  
  
-   <span data-ttu-id="b264b-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> 從 Unmanaged 緩衝區封送處理資料至 Managed 物件。</span><span class="sxs-lookup"><span data-stu-id="b264b-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>  
  
-   <span data-ttu-id="b264b-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> 用來釋放在結構中為字串保留的記憶體。</span><span class="sxs-lookup"><span data-stu-id="b264b-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>  
  
-   <span data-ttu-id="b264b-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> 用來釋放為陣列保留的記憶體。</span><span class="sxs-lookup"><span data-stu-id="b264b-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>  
  
 <span data-ttu-id="b264b-241">如先前所述，C# 允許 Unsafe 程式碼，而 [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] 則否。</span><span class="sxs-lookup"><span data-stu-id="b264b-241">As previously mentioned, C# allows unsafe code and [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] does not.</span></span> <span data-ttu-id="b264b-242">在 C# 範例中， `UsingUnsafePointer` 是一種替代的方法實作，會使用指標，而非 <xref:System.Runtime.InteropServices.Marshal> 類別，以傳回包含 `MyUnsafeStruct` 結構的陣列。</span><span class="sxs-lookup"><span data-stu-id="b264b-242">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="b264b-243">宣告原型</span><span class="sxs-lookup"><span data-stu-id="b264b-243">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### <a name="calling-functions"></a><span data-ttu-id="b264b-244">呼叫函式</span><span class="sxs-lookup"><span data-stu-id="b264b-244">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="b264b-245">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b264b-245">See Also</span></span>  
 [<span data-ttu-id="b264b-246">使用平台叫用封送處理資料</span><span class="sxs-lookup"><span data-stu-id="b264b-246">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 [<span data-ttu-id="b264b-247">平台叫用資料類型</span><span class="sxs-lookup"><span data-stu-id="b264b-247">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="b264b-248">封送處理字串</span><span class="sxs-lookup"><span data-stu-id="b264b-248">Marshaling Strings</span></span>](../../../docs/framework/interop/marshaling-strings.md)  
 [<span data-ttu-id="b264b-249">封送處理類型的陣列</span><span class="sxs-lookup"><span data-stu-id="b264b-249">Marshaling Arrays of Types</span></span>](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)
