---
title: Label 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- Label
helpviewer_keywords:
- images [Windows Forms], displaying in labels
- labels
- Label control [Windows Forms], about Label control
ms.assetid: dcad7f44-11b7-4c55-b0c0-d984ade43d7d
ms.openlocfilehash: 1ca14553c7cb51d2b7a329950aeaec4c0439762a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745280"
---
# <a name="label-control-overview-windows-forms"></a>Label 控制項概觀 (Windows Form)
Windows Forms <xref:System.Windows.Forms.Label> 控制項是用來顯示使用者無法編輯的文字或影像。 它們可用來識別表單上的物件，以提供特定控制項在按一下時會執行的動作，例如，或顯示資訊以回應應用程式中的運行時間事件或進程。 例如，您可以使用標籤，將描述性標題加入文字方塊、清單方塊、下拉式方塊等。 您也可以撰寫程式碼來變更標籤所顯示的文字，以回應執行時間的事件。 例如，如果您的應用程式需要幾分鐘的時間來處理變更，您可以在標籤中顯示處理狀態訊息。  
  
## <a name="working-with-the-label-control"></a>使用標籤控制項  
 因為 <xref:System.Windows.Forms.Label> 控制項無法接收焦點，所以它也可以用來建立其他控制項的存取金鑰。 存取金鑰可讓使用者按下 ALT 鍵與存取金鑰來選取另一個控制項。 如需詳細資訊，請參閱[建立 Windows Forms 控制項的存取金鑰](how-to-create-access-keys-for-windows-forms-controls.md)和[如何：使用 Windows Forms 標籤控制項建立便捷鍵](how-to-create-access-keys-with-windows-forms-label-controls.md)。  
  
 標籤中顯示的標題會包含在 [<xref:System.Windows.Forms.Label.Text%2A>] 屬性中。 <xref:System.Windows.Forms.Label.TextAlign%2A> 屬性可讓您設定標籤中文字的對齊方式。 如需詳細資訊，請參閱[如何：設定 Windows Forms 控制項所顯示的文字](how-to-set-the-text-displayed-by-a-windows-forms-control.md)。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Label>
- [操作說明：調整 Windows Forms Label 控制項大小以適合其內容](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [操作說明：使用 Windows Forms Label 控制項建立便捷鍵](how-to-create-access-keys-with-windows-forms-label-controls.md)
