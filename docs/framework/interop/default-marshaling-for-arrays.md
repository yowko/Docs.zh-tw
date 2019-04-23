---
title: 陣列的預設封送處理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3eb5c9686f54bcaacef8d593f0ace4804d4ae60
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098217"
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="56933-102">陣列的預設封送處理</span><span class="sxs-lookup"><span data-stu-id="56933-102">Default Marshaling for Arrays</span></span>
<span data-ttu-id="56933-103">在包含整個 Managed 程式碼的應用程式中，Common Language Runtime 會將陣列類型傳遞為 In/Out 參數。</span><span class="sxs-lookup"><span data-stu-id="56933-103">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="56933-104">相較之下，Interop 封送處理器預設會將陣列傳遞為 In 參數。</span><span class="sxs-lookup"><span data-stu-id="56933-104">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="56933-105">使用[關聯最佳化](copying-and-pinning.md)，與相同 Apartment 中的物件互動時，Blittable 陣列可以操作為 In/Out 參數。</span><span class="sxs-lookup"><span data-stu-id="56933-105">With [pinning optimization](copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="56933-106">不過，如果您稍後將程式碼匯出至用來產生跨電腦 Proxy 的型別程式庫，並且使用該程式庫跨 Apartment 封送處理呼叫，則呼叫可以回復為實際 In 參數行為。</span><span class="sxs-lookup"><span data-stu-id="56933-106">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="56933-107">陣列本質上相當複雜，而且 Managed 與 Unmanaged 陣列之間的區別保證資訊比其他非 Blittable 類型還要多。</span><span class="sxs-lookup"><span data-stu-id="56933-107">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span>  
  
## <a name="managed-arrays"></a><span data-ttu-id="56933-108">Managed 陣列</span><span class="sxs-lookup"><span data-stu-id="56933-108">Managed Arrays</span></span>  
 <span data-ttu-id="56933-109">Managed 陣列類別可能會不同；不過，<xref:System.Array?displayProperty=nameWithType> 類別是所有陣列類型的基底類別。</span><span class="sxs-lookup"><span data-stu-id="56933-109">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="56933-110">**System.Array** 類別的屬性可以判斷陣列的順位、長度以及下限和上限，以及用來存取、排序、搜尋、複製和建立陣列的方法。</span><span class="sxs-lookup"><span data-stu-id="56933-110">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="56933-111">這些陣列類型是動態的，而且沒有基底類別庫中所定義的對應靜態類型。</span><span class="sxs-lookup"><span data-stu-id="56933-111">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="56933-112">很容易就會將每個項目類型和順位組合視為不同類型的陣列。</span><span class="sxs-lookup"><span data-stu-id="56933-112">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="56933-113">因此，一維整數陣列的類型與一維 Double 類型陣列不同。</span><span class="sxs-lookup"><span data-stu-id="56933-113">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="56933-114">同樣地，二維整數陣列與一維整數陣列不同。</span><span class="sxs-lookup"><span data-stu-id="56933-114">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="56933-115">比較類型時，不會考慮陣列界限。</span><span class="sxs-lookup"><span data-stu-id="56933-115">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="56933-116">如下表所示，任何 Managed 陣列執行個體都必須是特定項目類型、順位和下限。</span><span class="sxs-lookup"><span data-stu-id="56933-116">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="56933-117">Managed 陣列類型</span><span class="sxs-lookup"><span data-stu-id="56933-117">Managed array type</span></span>|<span data-ttu-id="56933-118">項目類型</span><span class="sxs-lookup"><span data-stu-id="56933-118">Element type</span></span>|<span data-ttu-id="56933-119">順位</span><span class="sxs-lookup"><span data-stu-id="56933-119">Rank</span></span>|<span data-ttu-id="56933-120">下限</span><span class="sxs-lookup"><span data-stu-id="56933-120">Lower bound</span></span>|<span data-ttu-id="56933-121">簽章標記法</span><span class="sxs-lookup"><span data-stu-id="56933-121">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|**<span data-ttu-id="56933-122">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="56933-122">ELEMENT_TYPE_ARRAY</span></span>**|<span data-ttu-id="56933-123">依類型指定。</span><span class="sxs-lookup"><span data-stu-id="56933-123">Specified by type.</span></span>|<span data-ttu-id="56933-124">依順位指定。</span><span class="sxs-lookup"><span data-stu-id="56933-124">Specified by rank.</span></span>|<span data-ttu-id="56933-125">選擇性依界限指定。</span><span class="sxs-lookup"><span data-stu-id="56933-125">Optionally specified by bounds.</span></span>|<span data-ttu-id="56933-126">*type* **[** *n*,*m* **]**</span><span class="sxs-lookup"><span data-stu-id="56933-126">*type* **[** *n*,*m* **]**</span></span>|  
|**<span data-ttu-id="56933-127">ELEMENT_TYPE_CLASS</span><span class="sxs-lookup"><span data-stu-id="56933-127">ELEMENT_TYPE_CLASS</span></span>**|<span data-ttu-id="56933-128">不明</span><span class="sxs-lookup"><span data-stu-id="56933-128">Unknown</span></span>|<span data-ttu-id="56933-129">不明</span><span class="sxs-lookup"><span data-stu-id="56933-129">Unknown</span></span>|<span data-ttu-id="56933-130">不明</span><span class="sxs-lookup"><span data-stu-id="56933-130">Unknown</span></span>|**<span data-ttu-id="56933-131">System.Array</span><span class="sxs-lookup"><span data-stu-id="56933-131">System.Array</span></span>**|  
|**<span data-ttu-id="56933-132">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="56933-132">ELEMENT_TYPE_SZARRAY</span></span>**|<span data-ttu-id="56933-133">依類型指定。</span><span class="sxs-lookup"><span data-stu-id="56933-133">Specified by type.</span></span>|<span data-ttu-id="56933-134">1</span><span class="sxs-lookup"><span data-stu-id="56933-134">1</span></span>|<span data-ttu-id="56933-135">0</span><span class="sxs-lookup"><span data-stu-id="56933-135">0</span></span>|<span data-ttu-id="56933-136">*type* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="56933-136">*type* **[** *n* **]**</span></span>|  
  
## <a name="unmanaged-arrays"></a><span data-ttu-id="56933-137">Unmanaged 陣列</span><span class="sxs-lookup"><span data-stu-id="56933-137">Unmanaged Arrays</span></span>  
 <span data-ttu-id="56933-138">Unmanaged 陣列是具有固定或變動長度的 COM 樣式安全陣列或 C 樣式陣列。</span><span class="sxs-lookup"><span data-stu-id="56933-138">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="56933-139">安全陣列是自我描述陣列，具有關聯陣列資料的類型、順位和界限。</span><span class="sxs-lookup"><span data-stu-id="56933-139">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="56933-140">C 樣式陣列是固定下限為 0 的一維類型陣列。</span><span class="sxs-lookup"><span data-stu-id="56933-140">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="56933-141">封送處理服務具有這兩種類型之陣列的有限支援。</span><span class="sxs-lookup"><span data-stu-id="56933-141">The marshaling service has limited support for both types of arrays.</span></span>  
  
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="56933-142">將陣列參數傳遞給 .NET 程式碼</span><span class="sxs-lookup"><span data-stu-id="56933-142">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="56933-143">從 Unmanaged 程式碼，可以將 C 樣式陣列和安全陣列以安全陣列或 C 樣式陣列形式傳遞給 .NET 程式碼。</span><span class="sxs-lookup"><span data-stu-id="56933-143">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="56933-144">下表顯示 Unmanaged 類型值和匯入的類型。</span><span class="sxs-lookup"><span data-stu-id="56933-144">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="56933-145">Unmanaged 類型</span><span class="sxs-lookup"><span data-stu-id="56933-145">Unmanaged type</span></span>|<span data-ttu-id="56933-146">匯入的類型</span><span class="sxs-lookup"><span data-stu-id="56933-146">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="56933-147">**SafeArray(** *Type* **)**</span><span class="sxs-lookup"><span data-stu-id="56933-147">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="56933-148">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="56933-148">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="56933-149">順位 = 1，下限 = 0。</span><span class="sxs-lookup"><span data-stu-id="56933-149">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="56933-150">只有在 Managed 簽章中提供時，才會知道大小。</span><span class="sxs-lookup"><span data-stu-id="56933-150">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="56933-151">不是順位 = 1 或下限 = 0 的安全陣列無法封送處理為 **SZARRAY**。</span><span class="sxs-lookup"><span data-stu-id="56933-151">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="56933-152">*Type*  **[]**</span><span class="sxs-lookup"><span data-stu-id="56933-152">*Type*  **[]**</span></span>|<span data-ttu-id="56933-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="56933-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="56933-154">順位 = 1，下限 = 0。</span><span class="sxs-lookup"><span data-stu-id="56933-154">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="56933-155">只有在 Managed 簽章中提供時，才會知道大小。</span><span class="sxs-lookup"><span data-stu-id="56933-155">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="56933-156">安全陣列</span><span class="sxs-lookup"><span data-stu-id="56933-156">Safe Arrays</span></span>  
 <span data-ttu-id="56933-157">將安全陣列從型別程式庫匯入至 .NET 組件時，會將陣列轉換成一維已知類型陣列 (例如 **int**)。</span><span class="sxs-lookup"><span data-stu-id="56933-157">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="56933-158">套用至參數的相同類型轉換規則也會套用至陣列項目。</span><span class="sxs-lookup"><span data-stu-id="56933-158">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="56933-159">例如，**BSTR** 類型的安全陣列變成 Managed 字串陣列，而變異值的安全陣列變成 Managed 物件陣列。</span><span class="sxs-lookup"><span data-stu-id="56933-159">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="56933-160">**SAFEARRAY** 項目類型擷取自型別程式庫，並儲存至 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉的 **SAFEARRAY** 值中。</span><span class="sxs-lookup"><span data-stu-id="56933-160">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="56933-161">因為無法從型別程式庫判斷安全陣列的順位和界限，所以順位會假設等於 1，而下限假設等於 0。</span><span class="sxs-lookup"><span data-stu-id="56933-161">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="56933-162">順位和界限必須定義於[型別程式庫匯入工具 (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) 所產生的 Managed 簽章中。</span><span class="sxs-lookup"><span data-stu-id="56933-162">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="56933-163">如果在執行階段傳遞給方法的順位不同，則會擲回 <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException>。</span><span class="sxs-lookup"><span data-stu-id="56933-163">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="56933-164">如果在執行階段傳遞的陣列類型不同，則會擲回 <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException>。</span><span class="sxs-lookup"><span data-stu-id="56933-164">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="56933-165">下列範例示範 Managed 和 Unmanaged 程式碼中的安全陣列。</span><span class="sxs-lookup"><span data-stu-id="56933-165">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 **<span data-ttu-id="56933-166">Unmanaged 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-166">Unmanaged signature</span></span>**  
  
```  
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 **<span data-ttu-id="56933-167">Managed 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-167">Managed signature</span></span>**  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_I4)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_DATE)> _   
   ar() As DateTime)  
Sub New3(ByRef <MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_BSTR)> _   
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_I4)] int[] ar) ;  
void New2([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_DATE)]   
   DateTime[] ar);  
void New3([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_BSTR)]   
   ref String[] ar);  
```  
  
 <span data-ttu-id="56933-168">如果修改 Tlbimp.exe 所產生的方法簽章以指出項目類型為 **ELEMENT_TYPE_ARRAY** 而非 **ELEMENT_TYPE_SZARRAY**，則可以將多維度或非零繫結的安全陣列封送處理至 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="56933-168">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="56933-169">或者，您可以搭配使用 **/sysarray** 參數與 Tlbimp.exe，以將所有陣列匯入為 <xref:System.Array?displayProperty=nameWithType> 物件。</span><span class="sxs-lookup"><span data-stu-id="56933-169">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="56933-170">如果所傳遞的陣列已知為多維度，您可以編輯 Tlbimp.exe 所產生的 Microsoft Intermediate Language (MSIL) 程式碼，然後重新進行編譯。</span><span class="sxs-lookup"><span data-stu-id="56933-170">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="56933-171">如需如何修改 MSIL 程式碼的詳細資訊，請參閱[自訂執行階段可呼叫包裝函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="56933-171">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="56933-172">C 樣式陣列</span><span class="sxs-lookup"><span data-stu-id="56933-172">C-Style Arrays</span></span>  
 <span data-ttu-id="56933-173">將 C 樣式陣列從型別程式庫匯入至 .NET 組件時，會將陣列轉換成 **ELEMENT_TYPE_SZARRAY**。</span><span class="sxs-lookup"><span data-stu-id="56933-173">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="56933-174">陣列項目類型取決於型別程式庫，並且在匯入期間保留。</span><span class="sxs-lookup"><span data-stu-id="56933-174">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="56933-175">套用至參數的相同轉換規則也會套用至陣列項目。</span><span class="sxs-lookup"><span data-stu-id="56933-175">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="56933-176">例如，**LPStr** 類型陣列會成為 **String** 類型陣列。</span><span class="sxs-lookup"><span data-stu-id="56933-176">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="56933-177">Tlbimp.exe 會擷取陣列項目類型，並將 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性套用至參數。</span><span class="sxs-lookup"><span data-stu-id="56933-177">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="56933-178">陣列順位會假設等於 1。</span><span class="sxs-lookup"><span data-stu-id="56933-178">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="56933-179">如果順位大於 1，會以資料行主要順序將陣列封送處理為一維陣列。</span><span class="sxs-lookup"><span data-stu-id="56933-179">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="56933-180">下限一律會等於 0。</span><span class="sxs-lookup"><span data-stu-id="56933-180">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="56933-181">型別程式庫可以包含固定或可變長度的陣列。</span><span class="sxs-lookup"><span data-stu-id="56933-181">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="56933-182">Tlbimp.exe 只能從型別程式庫中匯入固定長度陣列，因為型別程式庫缺少封送處理可變長度陣列所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="56933-182">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="56933-183">使用固定長度陣列，會從型別程式庫中匯入大小，並將其擷取於套用至參數的 **MarshalAsAttribute** 中。</span><span class="sxs-lookup"><span data-stu-id="56933-183">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="56933-184">您必須手動定義包含可變長度陣列的型別程式庫，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="56933-184">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 **<span data-ttu-id="56933-185">Unmanaged 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-185">Unmanaged signature</span></span>**  
  
```  
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 **<span data-ttu-id="56933-186">Managed 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-186">Managed signature</span></span>**  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.LPArray, SizeConst=10)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, SizeConst=200)> _  
   ar() As Double)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)> _  
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.LPArray, SizeConst=10)] int[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray, SizeConst=200)] double[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray,   
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)] String[] ar);  
```  
  
 <span data-ttu-id="56933-187">雖然您可以將 **size_is** 或 **length_is** 屬性套用至介面定義語言 (IDL) 來源中的陣列以將大小傳送至用戶端，但是 Microsoft 介面定義語言 (MIDL) 編譯器不會將該資訊傳播至型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="56933-187">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="56933-188">如果不知道大小，Interop 封送處理服務無法封送處理陣列項目。</span><span class="sxs-lookup"><span data-stu-id="56933-188">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="56933-189">因此，會將可變長度的陣列匯入為參考引數。</span><span class="sxs-lookup"><span data-stu-id="56933-189">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="56933-190">例如：</span><span class="sxs-lookup"><span data-stu-id="56933-190">For example:</span></span>  
  
 **<span data-ttu-id="56933-191">Unmanaged 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-191">Unmanaged signature</span></span>**  
  
```  
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 **<span data-ttu-id="56933-192">Managed 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-192">Managed signature</span></span>**  
  
```vb  
Sub New1(ByRef ar As Integer)  
Sub New2(ByRef ar As Double)  
Sub New3(ByRef ar As String)  
```  
  
```csharp  
void New1(ref int ar);    
void New2(ref double ar);    
void New3(ref String ar);   
```  
  
 <span data-ttu-id="56933-193">您可以編輯 Tlbimp.exe 所產生的 Microsoft Intermediate Language (MSIL) 程式碼，然後重新進行編譯，以提供具有陣列大小的封送處理器。</span><span class="sxs-lookup"><span data-stu-id="56933-193">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="56933-194">如需如何修改 MSIL 程式碼的詳細資料，請參閱[自訂執行階段可呼叫包裝函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="56933-194">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span> <span data-ttu-id="56933-195">若要指出陣列中的項目數，請使用下列其中一種方式，將 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 類型套用至 Managed 方法定義的陣列參數：</span><span class="sxs-lookup"><span data-stu-id="56933-195">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
-   <span data-ttu-id="56933-196">識別包含陣列中項目數的另一個參數。</span><span class="sxs-lookup"><span data-stu-id="56933-196">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="56933-197">參數是以位置進行識別，而第一個參數開始於數字 0。</span><span class="sxs-lookup"><span data-stu-id="56933-197">The parameters are identified by position, starting with the first parameter as number 0.</span></span>     
  
    ```vb  
    Sub [New](ElemCnt As Integer, _  
       \<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       int ElemCnt,   
       [MarshalAs(UnmanagedType.LPArray, SizeParamIndex=0)] int[] ar );  
    ```  
  
-   <span data-ttu-id="56933-198">將陣列的大小定義為常數。</span><span class="sxs-lookup"><span data-stu-id="56933-198">Define the size of the array as a constant.</span></span> <span data-ttu-id="56933-199">例如：</span><span class="sxs-lookup"><span data-stu-id="56933-199">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="56933-200">將陣列從 Unmanaged 程式碼封送處理至 Managed 程式碼時，封送處理器會檢查與判斷陣列大小的參數建立關聯的 **MarshalAsAttribute**。</span><span class="sxs-lookup"><span data-stu-id="56933-200">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="56933-201">如果未指定陣列大小，則只能封送處理一個項目。</span><span class="sxs-lookup"><span data-stu-id="56933-201">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56933-202">**MarshalAsAttribute** 不會影響從 Managed 陣列封送處理至 Unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="56933-202">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="56933-203">在該方向，陣列大小取決於檢查。</span><span class="sxs-lookup"><span data-stu-id="56933-203">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="56933-204">沒有任何方法可以封送處理 Managed 陣列的子集。</span><span class="sxs-lookup"><span data-stu-id="56933-204">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="56933-205">Interop 封送處理器使用 **CoTaskMemAlloc** 和 **CoTaskMemFree** 方法來配置和擷取記憶體。</span><span class="sxs-lookup"><span data-stu-id="56933-205">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="56933-206">Unmanaged 程式碼所執行的記憶體配置也必須使用這些方法。</span><span class="sxs-lookup"><span data-stu-id="56933-206">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
## <a name="passing-arrays-to-com"></a><span data-ttu-id="56933-207">將陣列傳遞給 COM</span><span class="sxs-lookup"><span data-stu-id="56933-207">Passing Arrays to COM</span></span>  
 <span data-ttu-id="56933-208">所有 Managed 陣列類型都可以從 Managed 程式碼傳遞至 Unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="56933-208">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="56933-209">根據 Managed 類型和其套用的屬性，陣列可以存取為安全陣列或 C 樣式陣列，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="56933-209">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="56933-210">Managed 陣列類型</span><span class="sxs-lookup"><span data-stu-id="56933-210">Managed array type</span></span>|<span data-ttu-id="56933-211">匯出為</span><span class="sxs-lookup"><span data-stu-id="56933-211">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="56933-212">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span><span class="sxs-lookup"><span data-stu-id="56933-212">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<xref:System.Runtime.InteropServices.UnmanagedType> <span data-ttu-id="56933-213">**.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="56933-213">**.SafeArray(** *type* **)**</span></span><br /><br /> **<span data-ttu-id="56933-214">UnmanagedType.LPArray</span><span class="sxs-lookup"><span data-stu-id="56933-214">UnmanagedType.LPArray</span></span>**<br /><br /> <span data-ttu-id="56933-215">類型是在簽章中提供。</span><span class="sxs-lookup"><span data-stu-id="56933-215">Type is provided in the signature.</span></span> <span data-ttu-id="56933-216">順位一律為 1，下限一律為 0。</span><span class="sxs-lookup"><span data-stu-id="56933-216">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="56933-217">在執行階段，一律會知道大小。</span><span class="sxs-lookup"><span data-stu-id="56933-217">Size is always known at run time.</span></span>|  
|<span data-ttu-id="56933-218">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span><span class="sxs-lookup"><span data-stu-id="56933-218">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="56933-219">**UnmanagedType.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="56933-219">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> **<span data-ttu-id="56933-220">UnmanagedType.LPArray</span><span class="sxs-lookup"><span data-stu-id="56933-220">UnmanagedType.LPArray</span></span>**<br /><br /> <span data-ttu-id="56933-221">在簽章中，提供類型、順位和界限。</span><span class="sxs-lookup"><span data-stu-id="56933-221">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="56933-222">在執行階段，一律會知道大小。</span><span class="sxs-lookup"><span data-stu-id="56933-222">Size is always known at run time.</span></span>|  
|<span data-ttu-id="56933-223">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span><span class="sxs-lookup"><span data-stu-id="56933-223">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span></span>|**<span data-ttu-id="56933-224">UT_Interface</span><span class="sxs-lookup"><span data-stu-id="56933-224">UT_Interface</span></span>**<br /><br /> <span data-ttu-id="56933-225">**UnmanagedType.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="56933-225">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="56933-226">在執行階段，一律可辨識類型、順位、界限和大小。</span><span class="sxs-lookup"><span data-stu-id="56933-226">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="56933-227">與包含 LPSTR 或 LPWSTR 之結構陣列有關的 OLE Automation 限制。</span><span class="sxs-lookup"><span data-stu-id="56933-227">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="56933-228">因此，必須將 [字串] 欄位封送處理為 **UnmanagedType.BSTR**。</span><span class="sxs-lookup"><span data-stu-id="56933-228">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="56933-229">否則便會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="56933-229">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="elementtypeszarray"></a><span data-ttu-id="56933-230">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="56933-230">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="56933-231">將包含 **ELEMENT_TYPE_SZARRAY** 參數 (一維陣列) 的方法從 .NET 組件匯出至型別程式庫時，會將陣列參數轉換成指定類型的 **SAFEARRAY**。</span><span class="sxs-lookup"><span data-stu-id="56933-231">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="56933-232">相同的轉換規則會套用至陣列項目類型。</span><span class="sxs-lookup"><span data-stu-id="56933-232">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="56933-233">Managed 陣列的內容會自動從 Managed 記憶體複製至 **SAFEARRAY**。</span><span class="sxs-lookup"><span data-stu-id="56933-233">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="56933-234">例如：</span><span class="sxs-lookup"><span data-stu-id="56933-234">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="56933-235">Managed 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-235">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="56933-236">Unmanaged 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-236">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="56933-237">安全陣列的順位一律為 1，而下限一律為 0。</span><span class="sxs-lookup"><span data-stu-id="56933-237">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="56933-238">在執行階段，大小取決於所傳遞 Managed 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="56933-238">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="56933-239">使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性，也可以將陣列封送處理為 C 樣式陣列。</span><span class="sxs-lookup"><span data-stu-id="56933-239">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="56933-240">例如：</span><span class="sxs-lookup"><span data-stu-id="56933-240">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="56933-241">Managed 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-241">Managed signature</span></span>  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As Long, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]   
   long [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]   
   String [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, ArraySubType=   
   UnmanagedType.LPStr, SizeParamIndex=1)]   
   String [] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="56933-242">Unmanaged 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-242">Unmanaged signature</span></span>  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="56933-243">雖然封送處理器具有封送處理陣列所需的長度資訊，但是陣列長度通常會傳遞為個別引數，以將長度傳遞給被呼叫者。</span><span class="sxs-lookup"><span data-stu-id="56933-243">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="elementtypearray"></a><span data-ttu-id="56933-244">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="56933-244">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="56933-245">將包含 **ELEMENT_TYPE_ARRAY** 參數的方法從 .NET 組件匯出至型別程式庫時，會將陣列參數轉換成指定類型的 **SAFEARRAY**。</span><span class="sxs-lookup"><span data-stu-id="56933-245">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="56933-246">Managed 陣列的內容會自動從 Managed 記憶體複製至 **SAFEARRAY**。</span><span class="sxs-lookup"><span data-stu-id="56933-246">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="56933-247">例如：</span><span class="sxs-lookup"><span data-stu-id="56933-247">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="56933-248">Managed 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-248">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="56933-249">Unmanaged 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-249">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="56933-250">在執行階段，安全陣列的順位、大小和界限是取決於 Managed 陣列的特性。</span><span class="sxs-lookup"><span data-stu-id="56933-250">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="56933-251">套用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性，也可以將陣列封送處理為 C 樣式陣列。</span><span class="sxs-lookup"><span data-stu-id="56933-251">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="56933-252">例如：</span><span class="sxs-lookup"><span data-stu-id="56933-252">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="56933-253">Managed 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-253">Managed signature</span></span>  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex:=1)> _  
   ar(,) As Long, size As Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, _  
   ArraySubType:=UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar(,) As String, size As Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex=1)]   
   long [,] ar, int size );  
void New([MarshalAs(UnmanagedType.LPARRAY,   
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex=1)]   
   String [,] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="56933-254">Unmanaged 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-254">Unmanaged signature</span></span>  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="56933-255">無法封送處理巢狀陣列。</span><span class="sxs-lookup"><span data-stu-id="56933-255">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="56933-256">例如，下列簽章會在使用[型別程式庫匯出工具 (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) 匯出時產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="56933-256">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="56933-257">Managed 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-257">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="elementtypeclass-systemarray"></a><span data-ttu-id="56933-258">ELEMENT_TYPE_CLASS \<System.Array></span><span class="sxs-lookup"><span data-stu-id="56933-258">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="56933-259">將包含 <xref:System.Array?displayProperty=nameWithType> 參數的方法從 .NET 組件匯出至型別程式庫時，會將陣列參數轉換成 **_Array** 介面。</span><span class="sxs-lookup"><span data-stu-id="56933-259">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="56933-260">Managed 陣列的內容只能透過 **_Array** 介面的方法和屬性進行存取。</span><span class="sxs-lookup"><span data-stu-id="56933-260">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="56933-261">使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性，也可以將 **System.Array** 封送處理為 **SAFEARRAY**。</span><span class="sxs-lookup"><span data-stu-id="56933-261">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="56933-262">封送處理為安全陣列時，會將陣列項目封送處理為變異值。</span><span class="sxs-lookup"><span data-stu-id="56933-262">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="56933-263">例如：</span><span class="sxs-lookup"><span data-stu-id="56933-263">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="56933-264">Managed 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-264">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="56933-265">Unmanaged 簽章</span><span class="sxs-lookup"><span data-stu-id="56933-265">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="56933-266">結構內的陣列</span><span class="sxs-lookup"><span data-stu-id="56933-266">Arrays within Structures</span></span>  
 <span data-ttu-id="56933-267">Unmanaged 結構可以包含內嵌的陣列。</span><span class="sxs-lookup"><span data-stu-id="56933-267">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="56933-268">根據預設，會將這些內嵌的陣列欄位封送處理為 SAFEARRAY。</span><span class="sxs-lookup"><span data-stu-id="56933-268">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="56933-269">在下列範例中，`s1` 是直接配置在結構本身內的內嵌陣列。</span><span class="sxs-lookup"><span data-stu-id="56933-269">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="56933-270">Unmanaged 呈現</span><span class="sxs-lookup"><span data-stu-id="56933-270">Unmanaged representation</span></span>  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="56933-271">陣列可以封送處理為 <xref:System.Runtime.InteropServices.UnmanagedType>，這需要您設定 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 欄位。</span><span class="sxs-lookup"><span data-stu-id="56933-271">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="56933-272">大小只能設定為常數。</span><span class="sxs-lookup"><span data-stu-id="56933-272">The size can be set only as a constant.</span></span> <span data-ttu-id="56933-273">下列程式碼示範 `MyStruct` 的對應 Managed 定義。</span><span class="sxs-lookup"><span data-stu-id="56933-273">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
```vb  
Public Structure <StructLayout(LayoutKind.Sequential)> MyStruct  
   Public <MarshalAs(UnmanagedType.ByValArray, SizeConst := 128)> _  
     s1() As Short  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MyStruct {  
   [MarshalAs(UnmanagedType.ByValArray, SizeConst=128)] public short[] s1;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="56933-274">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56933-274">See also</span></span>

- [<span data-ttu-id="56933-275">預設的封送處理行為</span><span class="sxs-lookup"><span data-stu-id="56933-275">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="56933-276">Blittable 和非 Blittable 類型</span><span class="sxs-lookup"><span data-stu-id="56933-276">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- [<span data-ttu-id="56933-277">方向屬性</span><span class="sxs-lookup"><span data-stu-id="56933-277">Directional Attributes</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [<span data-ttu-id="56933-278">複製和 Pin</span><span class="sxs-lookup"><span data-stu-id="56933-278">Copying and Pinning</span></span>](copying-and-pinning.md)
