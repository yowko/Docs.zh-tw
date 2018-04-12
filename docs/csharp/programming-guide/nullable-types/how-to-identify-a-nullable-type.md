---
title: 如何：識別可為 Null 的類型 (C# 程式設計手冊)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
caps.latest.revision: 7
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 610ed18308df02c5632361cd09ef94330dea598b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a><span data-ttu-id="a09bc-102">如何：識別可為 Null 的類型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="a09bc-102">How to: Identify a Nullable Type (C# Programming Guide)</span></span>
<span data-ttu-id="a09bc-103">您可以使用 C# [typeof](../../../csharp/language-reference/keywords/typeof.md) 運算子來建立代表可為 Null 類型的 <xref:System.Type> 物件：</span><span class="sxs-lookup"><span data-stu-id="a09bc-103">You can use the C# [typeof](../../../csharp/language-reference/keywords/typeof.md) operator to create a <xref:System.Type> object that represents a Nullable type:</span></span>  
  
```  
System.Type type = typeof(int?);  
```  
  
 <span data-ttu-id="a09bc-104">您也可以使用 <xref:System.Reflection> 命名空間的類別和方法，產生代表可為 Null 類型的 <xref:System.Type> 物件。</span><span class="sxs-lookup"><span data-stu-id="a09bc-104">You can also use the classes and methods of the <xref:System.Reflection> namespace to generate <xref:System.Type> objects that represent Nullable types.</span></span> <span data-ttu-id="a09bc-105">不過，如果您使用 <xref:System.Object.GetType%2A> 方法或 `is` 運算子嘗試在執行階段從可為 Null 的變數取得類型資訊，結果會是代表基礎類型的 <xref:System.Type>，不是可為 Null 的類型本身。</span><span class="sxs-lookup"><span data-stu-id="a09bc-105">However, if you try to obtain type information from Nullable variables at runtime by using the <xref:System.Object.GetType%2A> method or the `is` operator, the result is a <xref:System.Type> object that represents the underlying type, not the Nullable type itself.</span></span>  
  
 <span data-ttu-id="a09bc-106">當類型以隱含方式轉換成 <xref:System.Object> 時，在可為 Null 的類型上呼叫 `GetType`，會導致執行 boxing 作業。</span><span class="sxs-lookup"><span data-stu-id="a09bc-106">Calling `GetType` on a Nullable type causes a boxing operation to be performed when the type is implicitly converted to <xref:System.Object>.</span></span> <span data-ttu-id="a09bc-107">因此 <xref:System.Object.GetType%2A> 一律會傳回表示基礎類型的 <xref:System.Type> 物件，不是可為 Null 的類型。</span><span class="sxs-lookup"><span data-stu-id="a09bc-107">Therefore <xref:System.Object.GetType%2A> always returns a <xref:System.Type> object that represents the underlying type, not the Nullable type.</span></span>  
  
```  
int? i = 5;  
Type t = i.GetType();  
Console.WriteLine(t.FullName); //"System.Int32"  
```  
  
 <span data-ttu-id="a09bc-108">C# [是](../../../csharp/language-reference/keywords/is.md)運算子，也會在可為 Null 的基礎類型上運作。</span><span class="sxs-lookup"><span data-stu-id="a09bc-108">The C# [is](../../../csharp/language-reference/keywords/is.md) operator also operates on a Nullable's underlying type.</span></span> <span data-ttu-id="a09bc-109">因此，您無法使用 `is` 判斷變數是否是可為 Null 的類型。</span><span class="sxs-lookup"><span data-stu-id="a09bc-109">Therefore you cannot use `is` to determine whether a variable is a Nullable type.</span></span> <span data-ttu-id="a09bc-110">下例顯示 `is` 運算子將 Nullable\<int> 變數當做 int。</span><span class="sxs-lookup"><span data-stu-id="a09bc-110">The following example shows that the `is` operator treats a Nullable\<int> variable as an int.</span></span>  
  
```  
static void Main(string[] args)  
{  
  int? i = 5;  
  if (i is int) // true  
    //…  
}  
```  
  
## <a name="example"></a><span data-ttu-id="a09bc-111">範例</span><span class="sxs-lookup"><span data-stu-id="a09bc-111">Example</span></span>  
 <span data-ttu-id="a09bc-112">使用下列程式碼判斷 <xref:System.Type> 物件是否代表可為 Null 的類型。</span><span class="sxs-lookup"><span data-stu-id="a09bc-112">Use the following code to determine whether a <xref:System.Type> object represents a Nullable type.</span></span> <span data-ttu-id="a09bc-113">請記住，如果 `Type` 物件是從對 <xref:System.Object.GetType%2A> 的呼叫所傳回，這段程式碼一律會傳回 false，如本主題前文所述。</span><span class="sxs-lookup"><span data-stu-id="a09bc-113">Remember that this code always returns false if the `Type` object was returned from a call to <xref:System.Object.GetType%2A>, as explained earlier in this topic.</span></span>  
  
```  
if (type.IsGenericType && type.GetGenericTypeDefinition() == typeof(Nullable<>)) {…}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a09bc-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a09bc-114">See Also</span></span>  
 [<span data-ttu-id="a09bc-115">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="a09bc-115">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="a09bc-116">對可為 Null 的型別進行 boxing</span><span class="sxs-lookup"><span data-stu-id="a09bc-116">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)
