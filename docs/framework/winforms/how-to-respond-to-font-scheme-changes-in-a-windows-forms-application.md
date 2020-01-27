---
title: 回應 Windows Forms 應用程式中的字型配置變更
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: e3b96139a7cfd4b268d81b1da58229527e2beb87
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739222"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>如何：回應 Windows Forms 應用程式中的字型配置變更
在 Windows 作業系統中，使用者可以變更全系統的字型設定，讓預設字型顯示較大或較小。 變更這些字型設定對於視力受損的使用者而言非常重要，而且需要較大的類型來讀取其螢幕上的文字。 您可以藉由增加或減少表單的大小，以及每次字型配置變更時包含的所有文字，來調整 Windows Forms 應用程式以回應這些變更。 如果您想要讓表單以動態方式容納字型大小的變更，您可以將程式碼加入至表單。  
  
 一般而言，Windows Forms 使用的預設字型是 `GetStockObject(DEFAULT_GUI_FONT)`的 <xref:Microsoft.Win32> 命名空間呼叫所傳回的字型。 此呼叫傳回的字型只會在螢幕解析度變更時變更。 如下列程式所示，您的程式碼必須將預設字型變更為 <xref:System.Drawing.SystemFonts.IconTitleFont%2A>，以回應字型大小的變更。  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>若要使用桌面字型並回應字型配置變更  
  
1. 建立您的表單，並新增您想要的控制項。 如需詳細資訊，請參閱[如何：從命令列建立 Windows Forms 應用程式](how-to-create-a-windows-forms-application-from-the-command-line.md)和[要在 Windows Forms 上使用的控制項](./controls/controls-to-use-on-windows-forms.md)。  
  
2. 將 <xref:Microsoft.Win32> 命名空間的參考新增至您的程式碼。  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3. 將下列程式碼加入至表單的函式，以連結所需的事件處理常式，以及變更用於表單的預設字型。  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4. 執行 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> 事件的處理常式，讓表單在 <xref:Microsoft.Win32.UserPreferenceCategory.Window> 分類變更時自動調整。  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5. 最後，針對卸離 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> 事件處理常式的 <xref:System.Windows.Forms.Form.FormClosing> 事件，執行處理常式。  
  
     > [!IMPORTANT]
     > 若無法包含此程式碼，將會導致您的應用程式流失記憶體。  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6. 編譯並執行程式碼。  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>手動變更 Windows XP 中的字型配置  
  
1. 當您的 Windows Forms 應用程式正在執行時，請以滑鼠右鍵按一下 Windows 桌面，然後從快捷方式功能表中選擇 [**屬性**]。  
  
2. 在 [**顯示內容**] 對話方塊中，按一下 [**外觀**] 索引標籤。  
  
3. 從 [**字型大小**] 下拉式清單方塊中，選取新的字型大小。  
  
     您會發現表單現在會回應桌面字型配置中的執行時間變更。 當使用者在**標準**、**大**字型和**超大**字型之間變更時，表單會變更字型並正確縮放。  
  
## <a name="example"></a>範例  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 這個程式碼範例中的函式包含 `InitializeComponent`的呼叫，這是在 Visual Studio 中建立新的 Windows Forms 專案時所定義。 如果您要在命令列上建立應用程式，請移除這行程式碼。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [Windows Forms 中的自動縮放比例](automatic-scaling-in-windows-forms.md)
