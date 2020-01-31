---
title: 變更表單框線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: 2c8eb25b44c7406e4312f432f2d69524346f94d6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739561"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>如何：變更 Windows Form 的框線
在決定 Windows Form 的外觀和行為時，您有幾種框線樣式可以選擇。 藉由變更 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 屬性，您可以控制表單的調整大小行為。 此外，設定 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 也會影響標題列的顯示方式，以及所出現在標題列上的按鈕。 如需詳細資訊，請參閱<xref:System.Windows.Forms.FormBorderStyle>。  
  
 在 Visual Studio 中對於本工作有更詳盡的支援。  
  
 另請參閱[如何：使用設計工具變更 Windows Forms 的框線](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100))。  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>以程式設計方式設定 Windows Form 的框線樣式  
  
- 將 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 屬性設定為您想要的樣式。 下列程式碼範例會將表單 `DlgBx1` 的框線樣式設定為 <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>。  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     另請參閱[如何：在設計階段建立對話方塊](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100))。  
  
     此外，如果您已選擇提供選擇性**最小化**和**最大化**按鈕之表單的框線樣式，您可以指定是否要讓這兩個按鈕或兩者都正常運作。 當您想要密切控制使用者經驗時，這些按鈕會很有用。 預設會啟用 [**最小化**] 和 [**最大化**] 按鈕，而且其功能會透過 [**屬性**] 視窗來操作。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [Windows Forms 使用者入門](getting-started-with-windows-forms.md)
