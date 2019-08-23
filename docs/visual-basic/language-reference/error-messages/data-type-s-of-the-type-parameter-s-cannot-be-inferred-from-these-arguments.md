---
title: 無法從這些引數推斷類型參數的資料類型
ms.date: 07/20/2015
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
ms.openlocfilehash: 81535e3272eaed587288c26c4a4b9649467abed8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963556"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="e7e81-102">無法從這些引數推斷類型參數的資料類型</span><span class="sxs-lookup"><span data-stu-id="e7e81-102">Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>
<span data-ttu-id="e7e81-103">無法從這些引數推斷類型參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e7e81-103">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="e7e81-104">明確指定資料類型或許可以更正這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e7e81-104">Specifying the data type(s) explicitly might correct this error.</span></span>  
  
 <span data-ttu-id="e7e81-105">多載解析失敗時，會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e7e81-105">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="e7e81-106">它會顯示為附屬訊息，說明為什麼排除特定多載候選項目。</span><span class="sxs-lookup"><span data-stu-id="e7e81-106">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="e7e81-107">錯誤訊息說明編譯器無法使用類型推斷來尋找類型參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e7e81-107">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7e81-108">當無法指定引數時 (例如，針對查詢運算式中的查詢運算子)，會顯示不含第二句的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="e7e81-108">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>  
  
 <span data-ttu-id="e7e81-109">下列程式碼示範這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e7e81-109">The following code demonstrates the error.</span></span>  
  
```vb  
Module Module1  
  
    Sub Main()  
  
        '' Not Valid.  
        'OverloadedGenericMethod("Hello", "World")  
  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T)(ByVal x As String,   
                                      ByVal y As InterfaceExample(Of T))  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,   
                                         ByVal y As InterfaceExample(Of R))  
    End Sub  
  
End Module  
  
Interface InterfaceExample(Of T)  
End Interface  
```  
  
 <span data-ttu-id="e7e81-110">**錯誤識別碼:** BC36647 和 BC36644</span><span class="sxs-lookup"><span data-stu-id="e7e81-110">**Error ID:** BC36647 and BC36644</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e7e81-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e7e81-111">To correct this error</span></span>  
  
- <span data-ttu-id="e7e81-112">您可以指定一個或多個類型參數的資料類型，而不是依賴類型推斷。</span><span class="sxs-lookup"><span data-stu-id="e7e81-112">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7e81-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7e81-113">See also</span></span>

- [<span data-ttu-id="e7e81-114">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="e7e81-114">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="e7e81-115">Generic Procedures in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7e81-115">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="e7e81-116">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="e7e81-116">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
