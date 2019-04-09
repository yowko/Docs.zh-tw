---
title: 追蹤參數
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], trace switches
- trace switches, about trace switches
- tracing [.NET Framework], level of detail
- switches, trace
- trace switches
- trace switches, creating custom
ms.assetid: 8ab913aa-f400-4406-9436-f45bc6e54fbe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85a1a017197826717280f53995ed98f26f1d80bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132661"
---
# <a name="trace-switches"></a>追蹤參數
追蹤參數可讓您啟用、停用和篩選追蹤輸出。 它們是存在於您的程式碼中的物件，並可透過 .config 檔案在外部設定。 .NET Framework 中提供三種類型的追蹤參數： <xref:System.Diagnostics.BooleanSwitch> 類別、 <xref:System.Diagnostics.TraceSwitch> 類別和 <xref:System.Diagnostics.SourceSwitch> 類別。 <xref:System.Diagnostics.BooleanSwitch> 類別是做為切換參數，可啟用或停用各種追蹤陳述式。 <xref:System.Diagnostics.TraceSwitch> 和 <xref:System.Diagnostics.SourceSwitch> 類別可讓您針對特定追蹤層級啟用追蹤參數，以顯示針對該層級及其下所有層級指定的 <xref:System.Diagnostics.Trace> 或 <xref:System.Diagnostics.TraceSource> 訊息。 如果您停用此參數，就不會顯示追蹤訊息。 所有這些類別都是衍生自抽象 (**MustInherit**) 類別 **Switch**，如同任何使用者開發的參數。  
  
 追蹤參數對於篩選資訊很有用。 比方說，您可能想要查看資料存取模組中的每個追蹤訊息，但只查看應用程式其餘部分的錯誤訊息。 在此情況下，您會對資料存取模組使用一個追蹤參數，對應用程式的其餘部分使用一個參數。 使用 .config 檔案將參數設為適當的設定，即可控制您所接收的追蹤訊息類型。 如需詳細資訊，請參閱[如何：建立、 初始化和設定追蹤參數](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)。  
  
 一般而言，執行已部署的應用程式時，會停用其參數，這樣使用者就不需要觀察應用程式執行時，出現在螢幕上或塞滿記錄檔的許多無關的追蹤訊息。 如果在應用程式執行期間發生問題，您可以停止應用程式、啟用參數，並重新啟動應用程式。 然後就會顯示追蹤訊息。  
  
 若要使用參數，您必須先從 **BooleanSwitch** 類別、 **TraceSwitch** 類別或開發人員定義的參數類別建立參數物件。 如需建立開發人員定義參數的詳細資訊，請參閱 .NET Framework 參考中的 <xref:System.Diagnostics.Switch> 類別。 然後您可以設定組態值，指定何時要使用該參數物件。 再於各種 **Trace** (或 **Debug**) 追蹤方法中測試參數物件的設定。  
  
## <a name="trace-levels"></a>追蹤層級  
 當您使用 **TraceSwitch**時，還有其他考量。 **TraceSwitch** 物件有四個會傳回 **布林** 值的屬性，指出該參數是否至少設定為某個特定層級：  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 層級可讓您將所接收的追蹤資訊量，僅限於解決問題所需的資訊。 您可以將追蹤參數設為適當的追蹤層級，以指定您想要的追蹤輸出詳細程度。 您可以接收錯誤訊息、警告訊息、告知性訊息、詳細的追蹤訊息，或沒有任何訊息。  
  
 哪種訊息要與每個層級相關聯，完全由您決定。 一般而言，追蹤訊息的內容取決於與每個層級相關聯的項目，但您可以決定層級之間的差異。 例如，您可能想要提供問題層級 3 (**資訊**) 的詳細說明，但在層級 1 (**錯誤**) 只提供錯誤參考編號。 哪種配置最適合您的應用程式，完全由您決定。  
  
 這些屬性對應於 **TraceLevel** 列舉的值 1 到 4。 下表列出 **TraceLevel** 列舉及其值的層級。  
  
|列舉值|整數值|顯示的訊息類型 (或寫入至指定的輸出目標)|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|Off|0|None|  
|錯誤|1|只有錯誤訊息|  
|警告|2|警告訊息和錯誤訊息|  
|資訊|3|告知性訊息、警告訊息和錯誤訊息|  
|詳細資訊|4|詳細資訊訊息、告知性訊息、警告訊息和錯誤訊息|  
  
 **TraceSwitch** 屬性會指出參數的最大追蹤層級。 也就是說，會針對所指定的層級以及其下所有層級寫入追蹤資訊。 例如，如果 **TraceInfo** 是 **true**，則 **TraceError** 和 **TraceWarning** 也是 **true** ，但 **TraceVerbose** 很可能是 **false**。  
  
 這些屬性是唯讀的。 設定 **TraceLevel** 屬性時， **TraceSwitch** 物件會自動設定這些屬性。 例如:   
  
```vb  
Dim myTraceSwitch As New TraceSwitch("SwitchOne", "The first switch")  
myTraceSwitch.Level = TraceLevel.Info  
' This message box displays true, because setting the level to  
' TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString())  
' This messagebox displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString())  
```  
  
```csharp  
System.Diagnostics.TraceSwitch myTraceSwitch =   
   new System.Diagnostics.TraceSwitch("SwitchOne", "The first switch");  
myTraceSwitch.Level = System.Diagnostics.TraceLevel.Info;  
// This message box displays true, because setting the level to   
// TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString());  
// This message box displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString());  
```  
  
## <a name="developer-defined-switches"></a>開發人員定義的參數  
 除了提供 **BooleanSwitch** 和 **TraceSwitch**，您也可以從 **Switch** 類別繼承，再以自訂的方法來覆寫基底類別方法，以定義自己的參數。 如需建立開發人員定義參數的詳細資訊，請參閱 .NET Framework 參考中的 <xref:System.Diagnostics.Switch> 類別。  
  
## <a name="see-also"></a>另請參閱

- [追蹤接聽項](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [HOW TO：將追蹤陳述式新增至應用程式程式碼](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [追蹤和稽核應用程式](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
