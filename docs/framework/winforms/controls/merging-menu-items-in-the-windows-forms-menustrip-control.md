---
title: 合併 MenuStrip 控制項中的功能表項目
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
ms.openlocfilehash: 9fc2b40ef23d72db51853c124095b734a7646cda
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739049"
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>合併 Windows Form MenuStrip 控制項中的功能表項目
如果您有多重文件介面（MDI）應用程式，您可以將子表單中的功能表項目或整個功能表合併到父表單的功能表中。  
  
 本主題描述與在 MDI 應用程式中合併功能表項目相關聯的基本概念。  
  
## <a name="general-concepts"></a>一般概念  
 合併套裝程式含目標和原始檔控制：  
  
- 目標是要在其中合併功能表項目的主要或 MDI 父表單上的 <xref:System.Windows.Forms.MenuStrip> 控制項。  
  
- 來源是 MDI 子表單上的 <xref:System.Windows.Forms.MenuStrip> 控制項，其中包含您要合併至目標功能表的功能表項目。  
  
 [<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>] 屬性會識別功能表項目，其下拉式清單會填入目前 MDI 父表單的 MDI 子系的標題。 例如，您通常會列出目前在 [**視窗]** 功能表上開啟的 MDI 子系。  
  
 <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> 屬性會識別哪些功能表項目來自 MDI 子表單上的 <xref:System.Windows.Forms.MenuStrip>。  
  
 您可以手動或自動合併功能表項目。 這兩種方法的功能表項目會以相同的方式進行合併，但合併會以不同的方式啟動，如本主題稍後的「手動合併」和「自動合併」章節所述。 在手動和自動合併中，每個合併動作都會影響下一個合併動作。  
  
 <xref:System.Windows.Forms.MenuStrip> 合併會將功能表項目從一個 <xref:System.Windows.Forms.ToolStrip> 移到另一個，而不是複製它們，就像 <xref:System.Windows.Forms.MainMenu>的情況一樣。  
  
## <a name="mergeaction-values"></a>MergeAction 值  
 您可以使用 <xref:System.Windows.Forms.MergeAction> 屬性，在來源 <xref:System.Windows.Forms.MenuStrip> 的功能表項目上設定合併動作。  
  
 下表描述可用合併動作的意義和一般用法。  
  
|MergeAction 值|描述|一般用法|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|預設將來源專案加入目標專案集合的結尾。|當程式的某些部分啟動時，將功能表項目加入至功能表的結尾。|  
|<xref:System.Windows.Forms.MergeAction.Insert>|在來源專案上設定的 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 屬性所指定的位置中，將來源專案加入目標專案的集合中。|當程式的某些部分啟動時，將功能表項目加入至功能表的中間或開頭。<br /><br /> 如果兩個功能表項目的 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 值都相同，則會以反向順序加入。 適當地設定 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 以保留原始訂單。|  
|<xref:System.Windows.Forms.MergeAction.Replace>|尋找文字相符專案，如果找不到文字相符專案，則使用 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 值，然後以 [來源] 功能表項目取代相符的 [目標] 功能表項目。|以相同名稱的來源功能表項目取代目標功能表項目，以執行不同的作業。|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|尋找文字相符專案，如果找不到文字相符專案，則使用 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 值，然後將來源中的所有下拉式功能表新增至目標。|建立功能表結構，將功能表項目插入或加入至子功能表，或從子功能表移除功能表項目。 例如，您可以將功能表項目從 MDI 子系加入至主 <xref:System.Windows.Forms.MenuStrip>[**另存**新檔] 功能表。<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly> 可讓您流覽功能表結構，而不需要採取任何動作。 它提供評估後續專案的方法。|  
|<xref:System.Windows.Forms.MergeAction.Remove>|尋找文字相符專案，如果找不到文字相符專案，則使用 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 值，然後從目標中移除該專案。|從目標 <xref:System.Windows.Forms.MenuStrip>中移除功能表項目。|  
  
## <a name="manual-merging"></a>手動合併  
 只有 <xref:System.Windows.Forms.MenuStrip> 控制項會參與自動合併。 若要結合其他控制項的專案（例如 <xref:System.Windows.Forms.ToolStrip> 和 <xref:System.Windows.Forms.StatusStrip> 控制項），您必須在程式碼中依需求呼叫 <xref:System.Windows.Forms.ToolStripManager.Merge%2A> 和 <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> 方法，以手動方式進行合併。  
  
## <a name="automatic-merging"></a>自動合併  
 您可以藉由啟用原始格式，為 MDI 應用程式使用自動合併。 若要在 MDI 應用程式中使用 <xref:System.Windows.Forms.MenuStrip>，請將 <xref:System.Windows.Forms.Form.MainMenuStrip%2A> 屬性設定為目標 <xref:System.Windows.Forms.MenuStrip>，以便在來源 <xref:System.Windows.Forms.MenuStrip> 上執行的合併動作會反映在目標 <xref:System.Windows.Forms.MenuStrip>中。  
  
 您可以藉由啟用 MDI 來源上的 <xref:System.Windows.Forms.MenuStrip>，來觸發自動合併。 啟用時，會將來源 <xref:System.Windows.Forms.MenuStrip> 合併至 MDI 目標。 新表單變成作用中時，會在最後一個表單上還原合併，並在新表單上觸發。 您可以視需要在每個 <xref:System.Windows.Forms.ToolStripItem>上設定 <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> 屬性，以及在每個 <xref:System.Windows.Forms.MenuStrip>上設定 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性來控制此行為。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- [MenuStrip 控制項](menustrip-control-windows-forms.md)
- [操作說明：使用 MenuStrip 建立 MDI 視窗清單](how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)
- [操作說明：設定 MDI 應用程式的自動功能表合併功能](how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
