---
title: "如何：覆寫 ToString 方法 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 2dde281d439a07d7736949294772a57e926eb587
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>如何：覆寫 ToString 方法 (C# 程式設計手冊)
C# 中的每個類別或結構都會隱含地繼承 <xref:System.Object> 類別。 因此，C# 中的每個物件都會取得 <xref:System.Object.ToString%2A> 方法，以傳回該物件的字串表示。 例如，所有 `int` 類型的變數都有 `ToString` 方法，並讓它們以字串傳回其內容︰  
  
 [!code-cs[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]  
  
 當您建立自訂類別或結構時，應該覆寫 <xref:System.Object.ToString%2A> 方法，以將您的類型資訊提供給用戶端程式碼。  
  
 如需如何使用 `ToString` 方法以使用格式字串和其他類型之自訂格式的資訊，請參閱[格式化類型](../../../standard/base-types/formatting-types.md)。  
  
> [!IMPORTANT]
>  當您決定要透過這種方法提供的資訊時，請考慮不受信任的程式碼是否要使用類別或結構。 請務必確定您未提供任何可能會遭惡意程式碼利用的資訊。  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a>在類別或結構中覆寫 ToString 方法  
  
1.  宣告具有下列修飾詞和傳回型別的 `ToString` 方法︰  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  實作方法，讓它傳回字串。  
  
     下列範例除了類別之特定執行個體的特定資料之外還會傳回類別名稱。  
  
     [!code-cs[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     您可以測試 `ToString` 方法，如下列程式碼範例所示：  
  
     [!code-cs[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IFormattable>   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [字串](../../../csharp/programming-guide/strings/index.md)   
 [string](../../../csharp/language-reference/keywords/string.md)   
 [new](../../../csharp/language-reference/keywords/new.md)   
 [override](../../../csharp/language-reference/keywords/override.md)   
 [virtual](../../../csharp/language-reference/keywords/virtual.md)   
 [格式化類型](../../../standard/base-types/formatting-types.md)
