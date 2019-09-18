---
title: UI 自動化用戶端的控制項模式對應
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: cfd8e5dbe34df7b947646c714a360cf56b0435a4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043865"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>UI 自動化用戶端的控制項模式對應
> [!NOTE]
> 這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。  
  
 本主題列出控制項類型及其相關聯的控制項模式。  
  
 下表將控制項模式整理為下列類別：  
  
- 支援。 控制項必定支援此控制項模式。  
  
- 有條件支援。 控制項可依據控制項的狀態決定是否支援此控制項模式。  
  
- 不支援。 控制項不支援此控制項模式；自訂控制項可能支援此控制項模式。  
  
> [!NOTE]
> 有些控制項會依據其功能，有條件支援多種控制項模式。 例如，功能表項目控制項即依據其在功能表控制項中的功能，有條件支援 <xref:System.Windows.Automation.InvokePattern>、 <xref:System.Windows.Automation.ExpandCollapsePattern>、 <xref:System.Windows.Automation.TogglePattern>或 <xref:System.Windows.Automation.SelectionItemPattern> 控制項模式。  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>用戶端的 UI 自動化控制項模式  
  
|控制項類型|支援|有條件支援。|不支援|  
|------------------|---------------|-------------------------|-------------------|  
|按鈕|無|叫用、切換、展開摺疊|無|  
|行事曆|方格、表格|選取、捲軸|值|  
|核取方塊|Toggle|None|無|  
|下拉式方塊|展開摺疊|選取、值|Scroll|  
|資料格|Grid|捲軸、選取、表格|無|  
|Data Item|Selection Item|展開摺疊、方格項目、捲軸項目、表格、切換、值|None|  
|文件|文字|捲軸、值|None|  
|編輯|None|文字、範圍值、值|無|  
|群組|None|展開摺疊|無|  
|頁首|無|資料轉換|無|  
|標題項目|無|轉換、叫用|無|  
|超連結|叫用|值|None|  
|Image|無|方格項目、表格項目|叫用、選取項目|  
|清單|None|方格、多重檢視、捲軸、選取|資料表|  
|清單項目|Selection Item|展開摺疊、方格項目、叫用、捲軸項目 、切換、值|無|  
|功能表|無|None|無|  
|功能表列|無|展開摺疊、停駐、轉換|無|  
|功能表項目|無|展開摺疊、叫用、選取項目、切換|None|  
|窗格|無|停駐 捲軸、轉換|視窗|  
|進度列|無|範圍值、值|無|  
|選項按鈕|Selection Item|無|Toggle|  
|Scroll Bar|無|Range Value|Scroll|  
|Separator|無|None|None|  
|滑桿|無|範圍值、選取、值|無|  
|Spinner|None|範圍值、選取、值|None|  
|Split Button|叫用、展開摺疊|None|無|  
|狀態列|None|Grid|無|  
|索引標籤|選取|Scroll|None|  
|索引標籤項目|Selection Item|無|叫用|  
|資料表|方格、方格項目、表格、表格項目|無|無|  
|文字|無|方格項目、表格項目、文字|值|  
|Thumb|資料轉換|無|None|  
|標題列|無|None|無|  
|工具列|無|停駐、展開摺疊、轉換|無|  
|工具提示|無|文字、視窗|None|  
|樹狀結構|無|捲軸、選取|無|  
|樹狀目錄項目|展開摺疊|叫用、捲軸項目、選取項目、切換|None|  
|視窗|轉換、視窗|停駐|無|  
  
> [!NOTE]
> 如果控制項類型沒有所列的受支援控制項模式，但有一或多個有條件支援的控制項模式，就會一律支援其中一個條件式控制項模式。  
  
## <a name="see-also"></a>另請參閱

- [UI 自動化概觀](ui-automation-overview.md)
