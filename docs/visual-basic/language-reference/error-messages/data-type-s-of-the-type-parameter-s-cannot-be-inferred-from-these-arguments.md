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
ms.openlocfilehash: 91ee4bf9242df822890b0a171061f375a3b24cbc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803866"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="d3319-102">無法從這些引數推斷類型參數的資料類型</span><span class="sxs-lookup"><span data-stu-id="d3319-102">Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>
<span data-ttu-id="d3319-103">無法從這些引數推斷類型參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d3319-103">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="d3319-104">明確指定資料類型或許可以更正這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="d3319-104">Specifying the data type(s) explicitly might correct this error.</span></span>  
  
 <span data-ttu-id="d3319-105">多載解析失敗時，會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="d3319-105">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="d3319-106">它會顯示為附屬訊息，說明為什麼排除特定多載候選項目。</span><span class="sxs-lookup"><span data-stu-id="d3319-106">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="d3319-107">錯誤訊息說明編譯器無法使用類型推斷，來尋找資料型別之型別參數。</span><span class="sxs-lookup"><span data-stu-id="d3319-107">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3319-108">當無法指定引數時 (例如，針對查詢運算式中的查詢運算子)，會顯示不含第二句的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="d3319-108">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>  
  
 <span data-ttu-id="d3319-109">下列程式碼示範這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="d3319-109">The following code demonstrates the error.</span></span>  
  
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
  
 <span data-ttu-id="d3319-110">**錯誤 ID:** BC36647 和 BC36644</span><span class="sxs-lookup"><span data-stu-id="d3319-110">**Error ID:** BC36647 and BC36644</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d3319-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d3319-111">To correct this error</span></span>  
  
-   <span data-ttu-id="d3319-112">您可以指定一個或多個類型參數的資料類型，而不是依賴類型推斷。</span><span class="sxs-lookup"><span data-stu-id="d3319-112">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3319-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3319-113">See also</span></span>

- [<span data-ttu-id="d3319-114">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="d3319-114">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="d3319-115">Generic Procedures in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3319-115">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="d3319-116">在 Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="d3319-116">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
