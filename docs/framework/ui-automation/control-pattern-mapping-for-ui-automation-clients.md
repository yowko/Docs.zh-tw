---
title: "UI 自動化用戶端的控制項模式對應"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
caps.latest.revision: "18"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 31beb7ab9a978f5bb379a3c1d61c90c19c26ca6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>UI 自動化用戶端的控制項模式對應
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題列出控制項類型及其相關聯的控制項模式。  
  
 下表將控制項模式整理為下列類別：  
  
-   支援。 控制項必定支援此控制項模式。  
  
-   有條件支援。 控制項可依據控制項的狀態決定是否支援此控制項模式。  
  
-   不支援。 控制項不支援此控制項模式；自訂控制項可能支援此控制項模式。  
  
> [!NOTE]
>  有些控制項會依據其功能，有條件支援多種控制項模式。 例如，功能表項目控制項即依據其在功能表控制項中的功能，有條件支援 <xref:System.Windows.Automation.InvokePattern>、 <xref:System.Windows.Automation.ExpandCollapsePattern>、 <xref:System.Windows.Automation.TogglePattern>或 <xref:System.Windows.Automation.SelectionItemPattern> 控制項模式。  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>用戶端的 UI 自動化控制項模式  
  
|控制項類型|支援|有條件支援。|不支援|  
|------------------|---------------|-------------------------|-------------------|  
|按鈕|無|叫用、切換、展開摺疊|無|  
|行事曆|方格、表格|選取、捲軸|值|  
|核取方塊|Toggle|無|無|  
|下拉式方塊|展開摺疊|選取、值|Scroll|  
|資料格|Grid|捲軸、選取、表格|無|  
|Data Item|Selection Item|展開摺疊、方格項目、捲軸項目、表格、切換、值|無|  
|文件|Text|捲軸、值|無|  
|Edit|無|文字、範圍值、值|無|  
|群組|無|展開摺疊|無|  
|頁首|無|Transform|無|  
|標題項目|無|轉換、叫用|無|  
|超連結|叫用|值|無|  
|Image|無|方格項目、表格項目|叫用、選取項目|  
|清單|無|方格、多重檢視、捲軸、選取|資料表|  
|清單項目|Selection Item|展開摺疊、方格項目、叫用、捲軸項目 、切換、值|無|  
|功能表|無|無|無|  
|功能表列|無|展開摺疊、停駐、轉換|無|  
|功能表項目|無|展開摺疊、叫用、選取項目、切換|無|  
|窗格|無|停駐 捲軸、轉換|視窗|  
|進度列|無|範圍值、值|無|  
|選項按鈕|Selection Item|無|Toggle|  
|Scroll Bar|無|Range Value|Scroll|  
|Separator|無|無|無|  
|滑桿|無|範圍值、選取、值|無|  
|Spinner|無|範圍值、選取、值|無|  
|Split Button|叫用、展開摺疊|無|無|  
|狀態列|無|Grid|無|  
|索引標籤|選取|Scroll|無|  
|索引標籤項目|Selection Item|無|叫用|  
|資料表|方格、方格項目、表格、表格項目|無|無|  
|Text|無|方格項目、表格項目、文字|值|  
|Thumb|Transform|無|無|  
|標題列|無|無|無|  
|工具列|無|停駐、展開摺疊、轉換|無|  
|工具提示|無|文字、視窗|無|  
|樹狀結構|無|捲軸、選取|無|  
|樹狀目錄項目|展開摺疊|叫用、捲軸項目、選取項目、切換|無|  
|視窗|轉換、視窗|停駐|無|  
  
> [!NOTE]
>  如果控制項類型沒有所列的受支援控制項模式，但有一或多個有條件支援的控制項模式，就會一律支援其中一個條件式控制項模式。  
  
## <a name="see-also"></a>另請參閱  
 [UI 自動化概觀](../../../docs/framework/ui-automation/ui-automation-overview.md)
