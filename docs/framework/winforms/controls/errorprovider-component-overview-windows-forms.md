---
title: ErrorProvider 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
ms.openlocfilehash: 2272220917f2d5adf15f1ba84a5d4c3d0ec07165
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528882"
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider 元件概觀 (Windows Form)
Windows Form [ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-windows-forms.md)元件可用來驗證使用者輸入表單或控制項上的。 通常用於搭配驗證表單上的使用者輸入或顯示資料集內的錯誤。 錯誤提供者是較佳的替代方式比在訊息方塊中，顯示一則錯誤訊息，因為一旦關閉訊息方塊，錯誤訊息不再顯示。 <xref:System.Windows.Forms.ErrorProvider>元件會顯示錯誤圖示 (![ErrorProvider 圖示](../../../../docs/framework/winforms/controls/media/vberrorprovidericon.gif "vbErrorProviderIcon")) 相關的控制項，例如文字方塊; 當使用者透過將滑鼠指標旁邊錯誤圖示，工具提示隨即出現，顯示錯誤訊息字串。  
  
## <a name="key-properties"></a>索引鍵內容  
 <xref:System.Windows.Forms.ErrorProvider>元件的索引鍵屬性是<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>， <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>，和<xref:System.Windows.Forms.ErrorProvider.Icon%2A>。 當使用<xref:System.Windows.Forms.ErrorProvider>元件與資料繫結控制項<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>屬性必須設定為適當的容器 (通常是 Windows Form) 元件，以在表單上顯示錯誤圖示的順序。 當元件在設計師中，加入<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>屬性設定為包含表單; 如果您在程式碼中加入控制項，您必須自行設定。  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A>屬性可以設定為自訂的錯誤圖示，而不是預設值。 當<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>設定屬性，則<xref:System.Windows.Forms.ErrorProvider>元件可以顯示資料集的錯誤訊息。 主要方法<xref:System.Windows.Forms.ErrorProvider>元件是<xref:System.Windows.Forms.ErrorProvider.SetError%2A>方法，以指定的錯誤訊息字串和應該出現錯誤圖示的位置。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ErrorProvider>元件不支援內建的協助工具用戶端。 若要使用此元件時，讓您的應用程式可存取，您必須提供其他可存取回應機制。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ErrorProvider>  
 [操作說明：使用 Windows Forms ErrorProvider 元件檢視資料集錯誤](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)  
 [操作說明：使用 Windows Forms ErrorProvider 元件顯示表單驗證的錯誤圖示](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
