---
title: "如何：發行符合 .NET Framework 方針的事件 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
caps.latest.revision: 31
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
ms.openlocfilehash: 6d529e60643966fbabd5290543146977b4dc83c5
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>如何：發行符合 .NET Framework 方針的事件 (C# 程式設計手冊)
下列程序示範如何將遵循標準 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 模式的事件，新增至您的類別和結構。 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] Class Library 中的所有事件都是以定義如下的 <xref:System.EventHandler> 委派為基礎：  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)] 引進此委派的泛型版本 <xref:System.EventHandler%601>。 下列範例示範如何使用這兩種版本。  
  
 雖然您所定義之類別中的所有事件都能以任何有效的委派類型 (甚至是傳回值的委派) 為基礎，但通常建議您使用 <xref:System.EventHandler>，讓事件以 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 模式為基礎，如下列範例所示。  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>發行以 EventHandler 模式為基礎的事件  
  
1.  (如果您不需要傳送事件的自訂資料，請跳過此步驟，並前往步驟 3a。)以發行者和訂閱者類別可見的範圍，宣告自訂資料的類別。 然後新增必要的成員來保存自訂事件資料。 在此範例中，會傳回一個簡單的字串。  
  
    ```csharp  
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
  
2.  (如果您要使用 <xref:System.EventHandler%601> 的泛型版本，請跳過此步驟。)在發行類別中宣告委派。 指定名稱並以 *EventHandler* 作為結尾。 第二個參數指定自訂 EventArgs 類型。  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  使用下列其中一個步驟，在發行類別中宣告事件。  
  
    1.  如果沒有自訂 EventArgs 類別，Event 類型將會是非泛型的 EventHandler 委派。 因為當您建立 C# 專案時所包含的 <xref:System> 命名空間中已宣告委派，所以您不需要宣告委派。 將下列程式碼新增至發行者類別。  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  如果您使用的是 <xref:System.EventHandler> 的非泛型版本，而且有衍生自 <xref:System.EventArgs> 的自訂類別，請在發行類別內宣告事件，並使用步驟 2 中的委派作為類型。  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3.  如果您使用的是泛型版本，則不需要自訂委派。 相反地，您會在發行類別中將事件類型指定為 `EventHandler<CustomEventArgs>`，來替代角括號之間的類別名稱。  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a>範例  
 下列範例使用自訂 EventArgs 類別和 <xref:System.EventHandler%601> 作為事件類型，來示範上述步驟。  
  
 [!code-cs[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Delegate>   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [事件](../../../csharp/programming-guide/events/index.md)   
 [委派](../../../csharp/programming-guide/delegates/index.md)
