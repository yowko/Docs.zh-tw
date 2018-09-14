---
title: 如何：變更 Windows Form 的框線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: e04234b4f2f18738567c3f9846d8ae0c94780fcb
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45615907"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>如何：變更 Windows Form 的框線
在決定 Windows Form 的外觀和行為時，您有幾種框線樣式可以選擇。 藉由變更 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 屬性，您可以控制表單的調整大小行為。 此外，設定 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 也會影響標題列的顯示方式，以及所出現在標題列上的按鈕。 如需詳細資訊，請參閱<xref:System.Windows.Forms.FormBorderStyle>。  
  
 在 Visual Studio 中對於本工作有更詳盡的支援。  
  
 另請參閱[如何： 變更 Windows Form 使用設計工具的框線](https://msdn.microsoft.com/library/yettzh3e\(v=vs.110\))。  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>以程式設計方式設定 Windows Form 的框線樣式  
  
-   將 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 屬性設定為您想要的樣式。 下列程式碼範例設定表單的框線樣式`DlgBx1`至<xref:System.Windows.Forms.FormBorderStyle.FixedDialog>。  
  
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
  
     另請參閱[如何： 在設計階段建立對話方塊](https://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))。  
  
     此外，如果您選擇提供選擇性的表單的框線樣式**最小化**並**最大化**按鈕，您可以指定是否要一個或兩個按鈕的功能。 當您想要密切控制使用者經驗時，這些按鈕會很有用。 **最小化**並**最大化**根據預設，會啟用按鈕，而其功能透過操作**屬性**視窗。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.FormBorderStyle>  
 <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>  
 [Windows Forms 使用者入門](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
