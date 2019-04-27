---
title: HOW TO：回應 Windows Forms 應用程式中的字型配置變更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: 6aad851770fb886de5d5c00b544ac6eac2857e42
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801851"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>HOW TO：回應 Windows Forms 應用程式中的字型配置變更
在 Windows 作業系統中，使用者可以變更要顯示的預設字型放大或縮小的全系統字型設定。 變更這些字型設定是很重要的是視覺障礙者，而且需要較大的類型，以讀取在其螢幕上的文字的使用者。 您可以調整您的 Windows Forms 應用程式，來增加或減少大小的表單和內含的所有文字的字型配置變更時回應這些變更。 如果您想您的表單，以動態方式反應字型大小的變更，您可以在您的表單中加入程式碼。  
  
 一般而言，Windows Forms 所使用的預設字型是所傳回的字型<xref:Microsoft.Win32>命名空間呼叫`GetStockObject(DEFAULT_GUI_FONT)`。 這個呼叫所傳回的字型只會變更螢幕解析度變更時。 下列程序所示，您的程式碼必須變更的預設字型<xref:System.Drawing.SystemFonts.IconTitleFont%2A>回應以字型大小的變更。  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>使用桌面的字型和回應的字型配置變更  
  
1. 建立您的表單，並加入您想要的控制項。 如需詳細資訊，請參閱[如何：從命令列建立 Windows Forms 應用程式](how-to-create-a-windows-forms-application-from-the-command-line.md)並[使用 Windows Form 上的控制項](./controls/controls-to-use-on-windows-forms.md)。  
  
2. 將參考加入<xref:Microsoft.Win32>您的程式碼的命名空間。  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3. 下列程式碼加入您的表單來連結所需的事件處理常式，並變更表單的使用中的預設字型的建構函式。  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4. 實作的處理常式<xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>會導致表單自動調整的事件時<xref:Microsoft.Win32.UserPreferenceCategory.Window>類別目錄的變更。  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5. 最後，實作的處理常式<xref:System.Windows.Forms.Form.FormClosing>中斷連結的事件<xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>事件處理常式。  
  
     > [!IMPORTANT]
     > 包括此程式碼的失敗會導致您的應用程式會造成記憶體流失。  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6. 編譯並執行程式碼。  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>若要以手動方式變更 Windows XP 中的字型配置  
  
1. 當 Windows Forms 應用程式執行時，以滑鼠右鍵按一下 Windows 桌面上，然後選擇 **屬性**從捷徑功能表。  
  
2. 在 **顯示屬性** 對話方塊中，按一下**外觀** 索引標籤。  
  
3. 從**字型大小**下拉式清單方塊中，選取新的字型大小。  
  
     您會發現表單現在會回應在桌面的字型配置中的執行階段變更。 使用者之間的變更時**Normal**，**大字型**，並**超大型字**，表單變更字型，並正確地進行縮放。  
  
## <a name="example"></a>範例  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 此程式碼範例 constructer 包含呼叫`InitializeComponent`，也就是定義當您在 Visual Studio 中建立新的 Windows Forms 專案。 如果您要建置您的應用程式，在命令列上，請移除這行程式碼。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [Windows Forms 中的自動縮放比例](automatic-scaling-in-windows-forms.md)
