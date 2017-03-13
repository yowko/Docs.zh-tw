---
title: "如何：發行符合 .NET Framework 方針的事件 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "事件 [C#], 實作方針"
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# 如何：發行符合 .NET Framework 方針的事件 (C# 程式設計手冊)
下列程序會示範如何將採用標準 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 模式的事件加入至您的類別和結構 \(Struct\) 中。  [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 類別庫 \(Class Library\) 內的所有事件都是根據 <xref:System.EventHandler> 委派 \(Delegate\) 而建立，此委派定義如下：  
  
```  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong-md.md)] 引進此委派的泛型版本，即 <xref:System.EventHandler%601>。  下列範例說明如何使用兩種版本。  
  
 雖然您所定義之類別內的事件可以以任何有效的委派型別 \(包括傳回值的委派\) 為基礎，不過一般會建議您使用 <xref:System.EventHandler>，讓您的事件以 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 模式為基礎，如下列範例所示：  
  
### 若要根據 EventHandler 模式來發行事件  
  
1.  \(如果您不需要以事件傳送自訂的資料，請跳過這個步驟，並執行步驟 3a\)。 以發行者類別和訂閱者類別可見的範圍宣告您自訂資料的類別。  然後加入必要的成員來保存您的自訂事件資料。  在此範例中，會傳回一個簡單的字串。  
  
    ```  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }   
    }  
    ```  
  
2.  \(如果您正在使用 <xref:System.EventHandler%601> 的泛型版本，請跳過這個步驟\)。 在發行類別內宣告委派，  然後為它提供名稱，並以 *EventHandler* 做為結尾。  第二個參數會指定自訂的 EventArgs 型別。  
  
    ```  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  使用下列其中一個步驟，在發行類別內宣告事件。  
  
    1.  如果沒有自訂的 EventArgs 類別，則您的 Event 型別將會是非泛型的 EventHandler 委派。  您不需要宣告委派，因為它已在您建立 C\# 專案時所包含的 <xref:System> 命名空間內宣告。  加入下列程式碼至發行者類別。  
  
        ```  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  如果您是使用 <xref:System.EventHandler> 的非泛型版本，而且您擁有衍生自 <xref:System.EventArgs> 的自訂類別，請在發行類別內宣告事件，並使用步驟 2 中的委派當做型別。  
  
        ```  
        public event CustomEventHandler RaiseCustomEvent;  
  
        ```  
  
    3.  如果您正在使用泛型版本，則不需要使用自訂委派，  而是在發行類別中，將事件型別指定為 `EventHandler<CustomEventArgs>`，以取代角括弧內的類別名稱。  
  
        ```  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## 範例  
 下列範例將使用自訂 EventArgs 類別和 <xref:System.EventHandler%601> 做為事件類型示範前述步驟。  
  
 [!code-cs[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]  
  
## 請參閱  
 <xref:System.Delegate>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [事件](../../../csharp/programming-guide/events/index.md)   
 [委派](../../../csharp/programming-guide/delegates/index.md)