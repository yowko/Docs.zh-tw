---
title: 合併 Windows Form MenuStrip 控制項中的功能表項目
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
ms.openlocfilehash: 9a1f59a065faaa3a08a9d8a68973adb1faa5ed09
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64582925"
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>合併 Windows Form MenuStrip 控制項中的功能表項目
如果您有多個文件介面 (MDI) 應用程式時，您可以合併到父表單的功能表的功能表項目或從子表單的整個功能表。  
  
 本主題描述與合併 MDI 應用程式中的功能表項目相關聯的基本概念。  
  
## <a name="general-concepts"></a>一般概念  
 合併的程序牽涉到的目標和原始檔控制：  
  
- 目標是<xref:System.Windows.Forms.MenuStrip>main 或 MDI 父表單的項目，其中您要合併的功能表項目上的控制項。  
  
- 來源是<xref:System.Windows.Forms.MenuStrip>MDI 子表單，其中包含您想要合併到目標 功能表的功能表項目上的控制項。  
  
 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性會識別您將會填入目前的 MDI 標題的下拉式清單中父表單的 MDI 子視窗的功能表項目。 比方說，您通常會列出在目前開啟的 MDI 子系**視窗**功能表。  
  
 <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A>屬性會識別功能表項目來自於而<xref:System.Windows.Forms.MenuStrip>MDI 子表單上。  
  
 您可以在手動或自動合併功能表項目。 功能表項目合併這兩種方法中，相同的方式，但以不同的方式，本主題稍後的 「 手動合併 」 和 「 自動合併 」 各節中所述啟動合併。 手動和自動合併，每個合併動作會影響下一步 合併動作。  
  
 <xref:System.Windows.Forms.MenuStrip> 合併移動功能表項目從某個<xref:System.Windows.Forms.ToolStrip>到另一個而不是複製它們，如同使用<xref:System.Windows.Forms.MainMenu>。  
  
## <a name="mergeaction-values"></a>MergeAction 值  
 您在來源中的功能表項目上設定合併動作<xref:System.Windows.Forms.MenuStrip>使用<xref:System.Windows.Forms.MergeAction>屬性。  
  
 下表描述可用的合併動作的意義和一般使用。  
  
|MergeAction 值|描述|一般用法|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|（預設值）將來源項目加入至目標項目集合的結尾。|啟動程式的某個部分時，則您可以加入功能表的尾端功能表項目。|  
|<xref:System.Windows.Forms.MergeAction.Insert>|將來源項目加入至目標項目的集合，在所指定的位置<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>來源項目上設定的屬性。|啟動程式的某個部分時，請至中間或功能表的開頭加入功能表項目。<br /><br /> 如果值<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>相同的兩個功能表項目，它們會加入以反向順序。 設定<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>適當地保留原始的順序。|  
|<xref:System.Windows.Forms.MergeAction.Replace>|尋找文字的相符項目，或使用<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>值，如果沒有文字相符項目找到，則，然後再在 [來源] 功能表項目以取代 [比對的目標] 功能表項目。|取代來源功能表項目執行一些不同的工作相同名稱的目標 功能表項目。|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|尋找文字的相符項目，或使用<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>如果找到，則文字相符項目，並再將所有下拉式清單的項目從來源到目標值。|建置功能表結構來插入或將功能表項目新增到子功能表，或移除子功能表的功能表項目。 比方說，您可以加入功能表項目從 MDI 子表單的主要<xref:System.Windows.Forms.MenuStrip>**另存新檔**功能表。<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly> 可讓您導覽功能表結構，但不採取任何動作。 它可用來評估後續項目。|  
|<xref:System.Windows.Forms.MergeAction.Remove>|尋找文字的相符項目，或使用<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>值如果找到，則文字相符項目，且然後在目標中移除的項目。|功能表項目移除目標<xref:System.Windows.Forms.MenuStrip>。|  
  
## <a name="manual-merging"></a>手動合併  
 只有<xref:System.Windows.Forms.MenuStrip>控制項參與自動合併。 這類結合的其他控制項，項目<xref:System.Windows.Forms.ToolStrip>並<xref:System.Windows.Forms.StatusStrip>控制項，您必須合併它們以手動的方式，藉由呼叫<xref:System.Windows.Forms.ToolStripManager.Merge%2A>和<xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A>中您所需的程式碼的方法。  
  
## <a name="automatic-merging"></a>自動合併  
 您可以使用方式，啟用 「 來源 」 形式 MDI 應用程式的自動合併。 若要使用<xref:System.Windows.Forms.MenuStrip>MDI 應用程式中，設定<xref:System.Windows.Forms.Form.MainMenuStrip%2A>屬性到目標<xref:System.Windows.Forms.MenuStrip>合併動作執行來源上<xref:System.Windows.Forms.MenuStrip>會反映在目標<xref:System.Windows.Forms.MenuStrip>。  
  
 您可以觸發自動合併，藉由啟用<xref:System.Windows.Forms.MenuStrip>MDI 來源上。 在啟動過程中，來源<xref:System.Windows.Forms.MenuStrip>會合併到 MDI 目標。 當新的表單變成作用中時，合併就是還原最後一個表單上，而且未觸發新的表單上。 您可以設定來控制此行為<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A>屬性，視需要在每個<xref:System.Windows.Forms.ToolStripItem>，並藉由設定<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>上每個屬性<xref:System.Windows.Forms.MenuStrip>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- [MenuStrip 控制項](menustrip-control-windows-forms.md)
- [如何：使用 MenuStrip 建立 MDI 視窗清單](how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)
- [如何：設定 MDI 應用程式的自動功能表合併](how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
