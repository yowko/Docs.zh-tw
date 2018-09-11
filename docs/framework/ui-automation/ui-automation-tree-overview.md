---
title: UI 自動化樹狀目錄概觀
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 042f3f82a88e987131145f38c1d8f5ecfa8dc487
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339236"
---
# <a name="ui-automation-tree-overview"></a>UI 自動化樹狀目錄概觀
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 輔助技術產品和測試指令碼瀏覽[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]樹狀目錄，以收集的相關資訊[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]和其項目。  
  
 內[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]樹狀目錄中有為根元素 (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>)，表示目前的桌面，而其子項目代表應用程式視窗。 每一個子元素可以包含代表的項目[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]例如功能表、 按鈕、 工具列和清單方塊。 接著這些項目可以包含例如清單項目的項目。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]樹狀結構是固定的結構並不很少完全看到它因為它可能包含數千個項目。 其中的部分會在需要時建置，且它可能隨著加入、移動或移除項目而發生變更。  
  
 使用者介面自動化提供者支援[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]藉由實作所組成 （通常是裝載在視窗中） 的根和子樹狀結構片段中的項目間的導覽樹狀目錄。 不過，提供者並不涉及控制項之間的導覽。 這由管理[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]核心，使用來自預設視窗提供者的資訊。  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>自動化樹狀結構的檢視  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]樹狀結構可以進行篩選，建立只包含檢視<xref:System.Windows.Automation.AutomationElement>特定用戶端相關的物件。 此方法可讓用戶端自訂透過呈現結構[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]其特定需求。  
  
 用戶端有兩種方式可自訂檢視：藉由範圍和篩選。 範圍會定義檢視的範圍，從基底項目開始：例如，應用程式可能只想要尋找桌面的直接子系，或是應用程式視窗的所有下階。 篩選會定義要包含在檢視中的項目類型。  
  
 使用者介面自動化提供者支援藉由在項目，包括定義屬性篩選<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>和<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>屬性。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 提供三個預設檢視。 這些檢視是由執行的篩選類型所定義；任何檢視的範圍是由應用程式定義。 此外，應用程式可以在屬性套用其他篩選；例如，只在控制項檢視中包含啟用的控制項。  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>未經處理的檢視  
 未經處理檢視[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]樹狀結構是完整的樹狀結構的<xref:System.Windows.Automation.AutomationElement>桌面是根的物件。 未經處理的檢視會密切依循應用程式的原生程式設計結構，因此是最詳細的可用檢視。 它也是樹狀結構其他檢視的建置基底。 因為此檢視相依於基礎[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]架構、 的未經處理檢視[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]按鈕會有不同的未經處理檢視比[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 按鈕。  
  
 搜尋而不指定屬性的項目，或使用取得的未經處理檢視<xref:System.Windows.Automation.TreeWalker.RawViewWalker>來導覽樹狀。  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>控制項檢視  
 控制項檢視[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]樹狀結構會簡化輔助技術產品的工作描述[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]協助終端使用者與該使用者的應用程式互動因為它密切地對應到[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]結構觀察得到的使用者。  
  
 控制項檢視是未經處理檢視的子集。 它包含所有[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]從終端使用者瞭解為互動式或構成中控制項的邏輯結構的未經處理檢視的項目[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]。 範例[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]參與的邏輯結構的項目[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]，但不是互動式本身，例如清單檢視標頭、 工具列、 功能表和 [狀態] 列的項目容器。 只用於配置或裝飾性用途的非互動式項目都不會顯示在控制項檢視中。 例如只用來配置對話方塊中的控制項面板，但是本身不含任何資訊。 控制項檢視中會顯示的非互動式項目是對話方塊中具有資訊和靜態文字的圖形。 控制項檢視中所包含的非互動式項目無法接收鍵盤焦點。  
  
 取得的控制項檢視所搜尋項目具有<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>屬性設定為`true`，或使用<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>來導覽樹狀。  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>內容檢視  
 內容檢視[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]樹狀結構是子集的控制項檢視。 它包含[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]傳達真實資訊的使用者介面中的項目包括[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]項目可以接收鍵盤焦點和某些文字標籤不在[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]項目。 例如，下拉式清單方塊中的值會出現在內容檢視中，因為它們代表使用者所使用的資訊。 在內容檢視中，下拉式方塊和清單方塊都表示為集合[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]其中一個或多個可能的項目可選取的項目。 在內容檢視中，一個一律開啟，一個可展開和摺疊的這項事實並沒有關係，因為它是設計來顯示要呈現給使用者的資料，或內容。  
  
 [內容] 檢視的取得方式搜尋項目具有<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>屬性設定為`true`，或使用<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>來導覽樹狀。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Automation.AutomationElement>  
 [UI 自動化概觀](../../../docs/framework/ui-automation/ui-automation-overview.md)
