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
ms.openlocfilehash: 485e7a17073d72618b9599113179cddde748e697
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181177"
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider 元件概觀 (Windows Form)
Windows Forms [ErrorProvider](errorprovider-component-windows-forms.md)元件用來驗證使用者輸入，在表單或控制項上的。 通常用於搭配驗證在表單上的使用者輸入或顯示在資料集內的錯誤。 錯誤提供者會是較好的選擇，比在訊息方塊中，顯示一則錯誤訊息，因為一旦關閉訊息方塊，出現錯誤訊息不再顯示。 <xref:System.Windows.Forms.ErrorProvider>元件會顯示錯誤圖示 (![ErrorProvider 圖示](./media/vberrorprovidericon.gif "vbErrorProviderIcon")) 相關的控制項，例如文字方塊，使用者將滑鼠指標置於上時旁邊錯誤圖示時，工具提示隨即出現，顯示錯誤訊息字串。  
  
## <a name="key-properties"></a>索引鍵內容  
 <xref:System.Windows.Forms.ErrorProvider>元件的索引鍵屬性是<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>， <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>，和<xref:System.Windows.Forms.ErrorProvider.Icon%2A>。 使用時<xref:System.Windows.Forms.ErrorProvider>元件與資料繫結控制項<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>屬性必須設定為適當的容器 （通常為 Windows 表單），以在表單上顯示錯誤圖示之元件的順序。 在設計師中，加入元件時<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>屬性設定為包含表單; 如果您在程式碼中加入控制項，您必須自行設定。  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A>屬性可以設定為自訂的錯誤圖示，而不是預設值。 當<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>屬性設定，<xref:System.Windows.Forms.ErrorProvider>元件可以顯示資料集的錯誤訊息。 主要方法<xref:System.Windows.Forms.ErrorProvider>元件是<xref:System.Windows.Forms.ErrorProvider.SetError%2A>方法，以指定的錯誤訊息字串和錯誤圖示應該出現的位置。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ErrorProvider>元件不提供協助工具用戶端的內建支援。 若要讓您的應用程式存取，使用此元件時中,，您必須提供額外的、 可存取的意見反應機制。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ErrorProvider>
- [如何：資料集使用 Windows Forms ErrorProvider 元件檢視錯誤](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [如何：表單驗證，使用 Windows Forms ErrorProvider 元件顯示錯誤圖示](display-error-icons-for-form-validation-with-wf-errorprovider.md)
