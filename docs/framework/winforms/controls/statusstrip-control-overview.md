---
title: StatusStrip 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
ms.openlocfilehash: e40373dd05e59325cdb6c2272d5749f3828b0755
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864559"
---
# <a name="statusstrip-control-overview"></a>StatusStrip 控制項概觀
<xref:System.Windows.Forms.StatusStrip> 控制項會顯示 <xref:System.Windows.Forms.Form> 上正在檢視之物件或該物件之元件的相關資訊，或顯示與該物件在您的應用程式中作業相關的內容資訊。 一般而言，<xref:System.Windows.Forms.StatusStrip> 控制項是由 <xref:System.Windows.Forms.ToolStripStatusLabel> 物件所組成，其中每個物件會顯示文字和 (或) 圖示。 <xref:System.Windows.Forms.StatusStrip> 也可以包含 <xref:System.Windows.Forms.ToolStripDropDownButton>、<xref:System.Windows.Forms.ToolStripSplitButton> 和 <xref:System.Windows.Forms.ToolStripProgressBar> 控制項。  
  
 預設 <xref:System.Windows.Forms.StatusStrip> 沒有面板。 若要將面板加入 <xref:System.Windows.Forms.StatusStrip>，請使用 <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> 方法。  
  
 在 Visual Studio 中，已針對處理 <xref:System.Windows.Forms.StatusStrip> 項目和常用命令提供廣泛的支援。  
  
 另請參閱[StatusStrip 項目集合編輯器](https://msdn.microsoft.com/library/ms233631\(v=vs.110\))， [StatusStrip 工作對話方塊](https://msdn.microsoft.com/library/ms233642\(v=vs.110\))。  
  
 雖然 <xref:System.Windows.Forms.StatusStrip> 會取代及擴充舊版的 <xref:System.Windows.Forms.StatusBar> 控制項，但是您也可以選擇保留 <xref:System.Windows.Forms.StatusBar>，以提供回溯相容性及供未來使用。  
  
### <a name="important-statusstrip-members"></a>重要的 StatusStrip 成員  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|取得或設定值，表示 <xref:System.Windows.Forms.StatusStrip> 是否支援溢位功能。|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|取得或設定值，表示 <xref:System.Windows.Forms.StatusStrip> 是否會在其 <xref:System.Windows.Forms.ToolStripContainer> 中的兩端之間自動縮放。|  
  
### <a name="important-statusstrip-companion-classes"></a>重要的 StatusStrip 附屬類別  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|代表 <xref:System.Windows.Forms.StatusStrip> 控制項中的面板。|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|顯示關聯的 <xref:System.Windows.Forms.ToolStripDropDown>，使用者可從中選取單一項目。|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|代表由兩個部分組成的控制項，其中一部分是標準按鈕，另一部分是下拉式功能表。|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|顯示處理序的完成狀態。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
