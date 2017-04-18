---
title: "UI 自動化樹狀目錄概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自動化樹狀目錄"
  - "UI 自動化、 樹狀結構"
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
caps.latest.revision: 25
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 25
---
# UI 自動化樹狀目錄概觀
> [!NOTE]
>  這份文件適用於.NET Framework 開發人員想要使用 managed[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中定義的類別<xref:System.Windows.Automation>命名空間。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API: UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 輔助技術產品和測試指令碼瀏覽[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]樹狀目錄，以收集有關的資訊[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]和其項目。  
  
 內[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]有樹狀結構是根項目 (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>)，代表目前的桌面，而且其子元素代表應用程式視窗。 每個這些子元素可以包含項目代表項[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]功能表、 按鈕、 工具列和清單方塊等。 接著這些項目可以包含例如清單項目的項目。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]樹狀結構不固定的結構，而且很少出現在其軸中因為它可能包含數千個項目。 其中的部分會在需要時建置，且它可能隨著加入、移動或移除項目而發生變更。  
  
 UI 自動化提供者支援[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]藉由實作片段，其中包含的根目錄 （通常是裝載在視窗中） 和樹狀子目錄內的項目之間巡覽樹狀目錄。 不過，提供者並不涉及控制項之間的導覽。 這由[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]核心，使用預設的視窗提供者的資訊。  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>自動化樹狀的檢閱  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]可以篩選樹狀目錄中建立檢視，裡面只有<xref:System.Windows.Automation.AutomationElement>特定用戶端相關的物件。 這種方法可讓用戶端自訂結構呈現透過[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]其特定需求。  
  
 用戶端有兩種方式可自訂檢視：藉由範圍和篩選。 範圍會定義檢視的範圍，從基底項目開始：例如，應用程式可能只想要尋找桌面的直接子系，或是應用程式視窗的所有下階。 篩選會定義要包含在檢視中的項目類型。  
  
 UI 自動化提供者支援依項目，包括定義屬性篩選<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>和<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>屬性。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]提供三個預設檢視。 這些檢視是由執行的篩選類型所定義；任何檢視的範圍是由應用程式定義。 此外，應用程式可以在屬性套用其他篩選；例如，只在控制項檢視中包含啟用的控制項。  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>未經處理的檢視  
 未經處理檢視[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]樹狀結構是完整的樹狀結構的<xref:System.Windows.Automation.AutomationElement>桌面的根物件。 未經處理的檢視會密切依循應用程式的原生程式設計結構，因此是最詳細的可用檢視。 它也是樹狀結構其他檢視的建置基底。 因為此檢視相依於基礎[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]架構、 未經處理檢視[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 按鈕會有不同的原始檢視比[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 按鈕。  
  
 取得未經處理檢視的搜尋項目，而不指定屬性或使用<xref:System.Windows.Automation.TreeWalker.RawViewWalker>瀏覽樹狀目錄中。  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>控制項檢視  
 控制項檢視[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]樹狀結構能簡化輔助技術產品的工作描述[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]可幫助使用者與該使用者互動應用程式因為它會緊密對應至[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]使用者所認知的結構。  
  
 控制項檢視是未經處理檢視的子集。 它包含所有[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]使用者能夠了解做為互動式或參與之控制項的邏輯結構的未經處理檢視中的項目[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]。 範例[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]項目構成的邏輯結構[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]，但不是互動式本身，例如清單檢視標頭、 工具列、 功能表和狀態列上的項目容器。 只用於配置或裝飾性用途的非互動式項目都不會顯示在控制項檢視中。 例如只用來配置對話方塊中的控制項面板，但是本身不含任何資訊。 控制項檢視中會顯示的非互動式項目是對話方塊中具有資訊和靜態文字的圖形。 控制項檢視中所包含的非互動式項目無法接收鍵盤焦點。  
  
 控制項檢視藉由搜尋項目具有取得<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>屬性設定為`true`，或使用<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>瀏覽樹狀目錄中。  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>內容檢視  
 內容檢視[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]樹狀結構是控制項檢視的子集。 它包含[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]在使用者介面中，則為 true 的資訊傳遞的項目包括[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]項目可以接收鍵盤焦點和一些文字標籤不在[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]項目。 例如，下拉式清單方塊中的值會出現在內容檢視中，因為它們代表使用者所使用的資訊。 在內容檢視中，下拉式方塊和清單方塊都表示為一系列[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]項目供您選取一個或多個一個項目。 在內容檢視中，一個一律開啟，一個可展開和摺疊的這項事實並沒有關係，因為它是設計來顯示要呈現給使用者的資料，或內容。  
  
 藉由搜尋項目具有取得內容檢視<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>屬性設定為`true`，或使用<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>瀏覽樹狀目錄中。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Automation.AutomationElement>   
 [UI 自動化概觀](../../../docs/framework/ui-automation/ui-automation-overview.md)