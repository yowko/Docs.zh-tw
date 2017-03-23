---
title: "如何：覆寫 ToString 方法 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "繼承 [C#], 覆寫 OnPaint 和 ToString"
  - "ToString 方法, 在 C# 中覆寫"
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# 如何：覆寫 ToString 方法 (C# 程式設計手冊)
C\# 中的每一個類別與結構 \(Struct\) 都會隱含繼承 <xref:System.Object> 類別。  所以，C\# 中的每一個物件都會取得 <xref:System.Object.ToString%2A> 方法，這個方法會傳回代表物件的字串。  例如，型別 `int` 的所有變數都有 `ToString` 方法，使其能夠以字串的形式傳回本身的內容：  
  
 [!code-cs[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]  
  
 當您建立自訂的類別或結構 \(Struct\) 時，應該覆寫 <xref:System.Object.ToString%2A> 方法，以便提供與型別相關的資訊給用戶端程式碼。  
  
 如需如何使用格式字串和其他類型的自訂格式設定與`ToString`方法，請參閱[格式化類型](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md)。  
  
> [!IMPORTANT]
>  在決定要透過這個方法提供何種資訊時，請考慮類別或結構是否將會由未受信任的程式碼所使用。  請確定不會提供任何可讓惡意程式碼利用的資訊。  
  
### 若要在類別或結構內覆寫 ToString 方法  
  
1.  宣告具有下列修飾詞 \(Modifier\) 和傳回型別的 `ToString` 方法：  
  
    ```c#  
    public override string ToString(){}  
    ```  
  
2.  實作此方法，使其傳回字串。  
  
     除了此類別之特定執行個體 \(Instance\) 所特有的資料，下列範例也會傳回類別的名稱。  
  
     [!code-cs[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     您可以測試 `ToString` 方法，如下列範例程式碼所示：  
  
     [!code-cs[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]  
  
## 請參閱  
 <xref:System.IFormattable>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [字串](../../../csharp/programming-guide/strings/index.md)   
 [字串](../../../csharp/language-reference/keywords/string.md)   
 [new](../../../csharp/language-reference/keywords/new.md)   
 [override](../../../csharp/language-reference/keywords/override.md)   
 [虛擬](../../../csharp/language-reference/keywords/virtual.md)   
 [格式化類型](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md)