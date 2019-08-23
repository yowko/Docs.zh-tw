---
title: 作法：在 Windows Forms 中建立 Windows 檔案總管樣式的介面
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 34a5cd735c350688d9e83003806668e213932c85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960630"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>作法：在 Windows Forms 中建立 Windows 檔案總管樣式的介面
Windows Explorer 是應用程式的常見使用者介面選擇, 因為它已經很熟悉。

 Windows Explorer 基本上<xref:System.Windows.Forms.TreeView>是控制項<xref:System.Windows.Forms.ListView>和控制項, 分別位於不同的面板上。 這些面板可透過分隔器進行調整。 這種控制項的相片順序對於顯示和流覽資訊非常有效。

 下列步驟示範如何在類似 Windows Explorer 的表單中排列控制項。 它們不會示範如何新增 Windows Explorer 應用程式的檔案流覽功能。

## <a name="to-create-a-windows-explorer-style-windows-form"></a>建立 Windows Explorer 樣式的 Windows Form

1. 建立新的 Windows 應用程式專案  > (檔案 **新增** > **專案** > **視覺效果C#** 或**Visual Basic**  > **傳統桌面** >  **Windows Forms 應用程式**)。

2. 從 [**工具箱**]:

    1. <xref:System.Windows.Forms.SplitContainer>將控制項拖曳至表單上。

    2. 將控制項拖曳至**SplitterPanel1** (標示為**Panel1**之<xref:System.Windows.Forms.SplitContainer>控制項的面板)。 <xref:System.Windows.Forms.TreeView>

    3. 將控制項拖曳至**SplitterPanel2** (標示為**Panel2**之<xref:System.Windows.Forms.SplitContainer>控制項的面板)。 <xref:System.Windows.Forms.ListView>

3. 按下 CTRL 鍵並依序按一下, 以選取所有三個控制項。 當您選取<xref:System.Windows.Forms.SplitContainer>控制項時, 請按一下分隔欄, 而不是面板。

    > [!NOTE]
    > 請勿使用 [**編輯**] 功能表上的 [**全選**] 命令。 如果您這樣做, 下一個步驟所需的屬性將不會出現在 [**屬性**] 視窗中。

4. 在 [屬性] 視窗中，將 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Fill>。

5. 按 F5 執行應用程式。

     表單會顯示兩部分的使用者介面, 類似于 Windows Explorer。

    > [!NOTE]
    > 當您拖曳分隔器時, 面板會自行調整大小。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.SplitContainer>
- [如何：建立具有 Windows Forms 的多窗格使用者介面](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [如何：定義分割視窗中的調整大小和位置行為](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [如何：水準分割視窗](how-to-split-a-window-horizontally.md)
- [SplitContainer 控制項](splitcontainer-control-windows-forms.md)
