---
title: WF 中的活動撰寫選項
ms.date: 03/30/2017
ms.assetid: b9061f5f-12c3-47f0-adbe-1330e2714c94
ms.openlocfilehash: 219d759cd1390a83abfb90af509b21047085f6e9
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46529589"
---
# <a name="activity-authoring-options-in-wf"></a>WF 中的活動撰寫選項
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 提供了幾個建立自訂活動的選項。 用於撰寫指定活動的正確方法，要視所需的執行階段功能而定。  
  
## <a name="deciding-which-base-activity-class-to-use-for-authoring-custom-activities"></a>決定要用於撰寫自訂活動的基底活動類別  
 下表列出自訂活動基底類別中可用的功能。  
  
|基底活動類別|可用的功能|  
|-------------------------|------------------------|  
|<xref:System.Activities.Activity>|將系統提供的群組和自訂活動撰寫至複合活動。|  
|<xref:System.Activities.CodeActivity>|提供可覆寫的 <xref:System.Activities.CodeActivity%601.Execute%2A> 方法來實作命令式功能。 同時也會提供對追蹤、變數和引數的存取。|  
|<xref:System.Activities.NativeActivity>|提供 <xref:System.Activities.CodeActivity> 的所有功能，加上中止活動執行、取消子活動執行、使用書籤，以及排程活動、活動動作與功能等。|  
|<xref:System.Activities.DynamicActivity>|提供 DOM 式方法來建構具有 WF 設計工具的活動以及透過 <xref:System.ComponentModel.ICustomTypeDescriptor> 的執行階段機制，不必定義新型別即可建立新活動。|  
  
## <a name="authoring-activities-using-activity"></a>使用 Activity 撰寫活動  
 衍生自 <xref:System.Activities.Activity> 的活動會藉由組裝其他現有活動來撰寫功能。 這些活動可以是現有的自訂活動，與來自 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 活動庫的活動。 組裝這些活動是建立自訂功能最基本的方式。 當使用視覺設計環境來撰寫工作流程時，最常採用這個方法。  
  
## <a name="authoring-activities-using-codeactivity-or-asynccodeactivity"></a>使用 CodeActivity 或 AsyncCodeActivity 製作活動  
 衍生自 <xref:System.Activities.CodeActivity> 或 <xref:System.Activities.AsyncCodeActivity> 的活動，可覆寫包含自訂命令式程式碼的 <xref:System.Activities.CodeActivity%601.Execute%2A> 方法，以實作命令式功能。 由執行階段執行活動時，就會執行自訂程式碼。 以這種方式建立的活動可以存取自訂功能，但卻無法存取執行階段的所有功能，例如完整存取執行環境、排定子活動、書籤建立或支援 Cancel 或 Abort 方法。 當 <xref:System.Activities.CodeActivity> 執行時，其可存取執行環境的縮減版 (透過 <xref:System.Activities.CodeActivityContext> 或 <xref:System.Activities.AsyncCodeActivityContext> 類別)。 使用 <xref:System.Activities.CodeActivity> 建立的活動可存取引數與變數解析、延伸與追蹤。 非同步排程活動可使用 <xref:System.Activities.AsyncCodeActivity> 來進行。  
  
## <a name="authoring-activities-using-nativeactivity"></a>使用 NativeActivity 撰寫活動  
 衍生自 <xref:System.Activities.NativeActivity> 的活動，就像衍生自 <xref:System.Activities.CodeActivity> 的活動一樣，會覆寫 <xref:System.Activities.NativeActivity.Execute%2A> 來建立命令式功能，但也可透過傳遞至 <xref:System.Activities.NativeActivityContext> 方法的 <xref:System.Activities.NativeActivity.Execute%2A> 來存取工作流程執行階段的所有功能。 此內容可支援排定和取消子活動、執行 <xref:System.Activities.ActivityAction> 和 <xref:System.Activities.ActivityFunc%601> 物件、將交易流動到工作流程中、叫用非同步處理序、取消和中止執行、存取執行屬性和擴充，以及書籤 (恢復暫停工作流程的控點)。  
  
## <a name="authoring-activities-using-dynamicactivity"></a>使用 DynamicActivity 撰寫活動  
 與其他三種活動型別不同，新功能並非從 <xref:System.Activities.DynamicActivity> (類別已密封) 衍生新型別來建立，而是使用活動文件物件模型 (DOM)，將功能組裝成 <xref:System.Activities.DynamicActivity.Properties%2A> 和 <xref:System.Activities.DynamicActivity.Implementation%2A> 屬性來建立。  
  
## <a name="authoring-activities-that-return-a-result"></a>撰寫傳回結果的活動  
 許多活動都必須在執行過後傳回結果。 雖然永遠都可為了這個目的在活動上定義自訂的 <xref:System.Activities.OutArgument%601>，但我們還是建議改用 <xref:System.Activities.Activity%601>，或衍生自 <xref:System.Activities.CodeActivity%601> 或 <xref:System.Activities.NativeActivity%601>。 這裡每個基底類別都有活動可用來傳回值的 <xref:System.Activities.OutArgument%601> 具名「結果」。 唯有在只需要從活動傳回一個結果時，才應使用傳回結果的活動；如果需要傳回多個結果，請改用獨立的 <xref:System.Activities.OutArgument%601> 成員。
