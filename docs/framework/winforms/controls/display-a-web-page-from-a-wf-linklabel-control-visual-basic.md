---
title: HOW TO：從 Windows Forms LinkLabel 控制項顯示網頁 (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- LinkLabel1_LinkClicked
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Web pages [Windows Forms], displaying
- linking [Windows Forms], to Web pages from forms
- Windows Forms, linking to Web pages
- LinkLabel control [Windows Forms], examples
ms.assetid: 477a7398-5971-4de3-b24c-f49f32bdb28a
ms.openlocfilehash: 1be9ff06e749d14b46946e899c6ffb6c3a950d65
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170023"
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a>HOW TO：從 Windows Forms LinkLabel 控制項顯示網頁 (Visual Basic)
此範例會顯示在預設瀏覽器網頁當使用者按一下 Windows Form<xref:System.Windows.Forms.LinkLabel>控制項。  
  
## <a name="example"></a>範例  
  
```vb  
Private Sub Form1_Load(ByVal sender As System.Object, ByVal e _  
As System.EventArgs) Handles MyBase.Load  
    LinkLabel1.Text = "Click here to get more info."  
    LinkLabel1.Links.Add(6, 4, "www.microsoft.com")  
End Sub  
Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, ByVal _  
e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) Handles _  
LinkLabel1.LinkClicked  
    System.Diagnostics.Process.Start(e.Link.LinkData.ToString())  
End Sub  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   Windows 表單名為`Form1`。  
  
-   名為 `LinkLabel1` 的 <xref:System.Windows.Forms.LinkLabel> 控制項。  
  
-   作用中的網際網路連線。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 若要呼叫<xref:System.Diagnostics.Process.Start%2A>方法需要完全信任。 如需詳細資訊，請參閱<xref:System.Security.SecurityException>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.LinkLabel>
- [LinkLabel 控制項](linklabel-control-windows-forms.md)
