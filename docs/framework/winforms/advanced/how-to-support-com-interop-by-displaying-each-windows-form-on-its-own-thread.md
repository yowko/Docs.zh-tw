---
title: 如何：在自己的執行緒上顯示每個 Windows Form 以支援 COM Interop
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: c78bcc8d784fc481af2449f2d81cfde42891e7fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522885"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>如何：在自己的執行緒上顯示每個 Windows Form 以支援 COM Interop
您可以藉由在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 訊息迴圈上顯示表單來解決 COM 互通性問題，這可使用 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> 方法來建立。  
  
 若要讓 Windows Form 在 COM 用戶端應用程式正確運作，您必須在 Windows Form 訊息迴圈上執行表單。 若要執行此工作，請使用下列的其中一個方法：  
  
-   使用 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> 方法，以顯示 Windows Form。 如需詳細資訊，請參閱[如何：顯示 Windows Form 和 ShowDialog 方法以支援 COM Interop](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)。  
  
-   在個別執行緒上顯示每個 Windows Form。  
  
 沒有對 Visual Studio 中的這項功能有廣泛的支援。  
  
 另請參閱 [逐步解說：在自己的執行緒上顯示每個 Windows Form 以支援 COM Interop](http://msdn.microsoft.com/library/ms233639\(v=vs.110\))。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何在個別的執行緒上顯示表單，並呼叫 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> 方法在該執行緒上啟動 Windows Form 訊息幫浦。 若要使用此方法，您必須使用 <xref:System.Windows.Forms.Control.Invoke%2A> 方法封送處理任何呼叫至來自 Unmanaged 應用程式的表單。  
  
 此方法需要表單的每個執行個體使用它自己的訊息迴圈在自己的執行緒上執行。 在每個執行緒中，您不能執行一個以上的訊息迴圈。 因此，您無法變更用戶端應用程式的訊息迴圈。 不過，您可以修改 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 元件來啟動會使用自己的訊息迴圈之新執行緒。  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   請將 `COMForm`、 `Form1`和 `FormManager` 類型編譯至稱為 `COMWinform.dll`的組件中。 請使用 [Packaging an Assembly for COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)所述的其中一種方法來登錄 COM Interop 組件。 您現在可以在 Unmanaged 應用程式中使用該組件和對應的類型程式庫 (.tlb) 檔案。 例如，您可以使用類型程式庫做為 Visual Basic 6.0 可執行檔專案中的參考。  
  
## <a name="see-also"></a>另請參閱  
 [將 .NET Framework 元件公開給 COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [封裝 COM 的組件](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [向 COM 註冊組件](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [操作說明：顯示 Windows Forms 和 ShowDialog 方法以支援 COM Interop](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [Windows Forms 和 Unmanaged 應用程式概觀](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
