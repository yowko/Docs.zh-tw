---
title: 在 Windows Form 上裝載 ActiveX 控制項的考慮因素
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
ms.openlocfilehash: a5e8e023da0eeebf5185f57eb51aa796f6f03a1a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639337"
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a>在 Windows Form 上裝載 ActiveX 控制項的考慮因素
雖然 Windows Forms 已進行最佳化來裝載 Windows Forms 控制項，但是您仍然可以使用 ActiveX 控制項。 規劃使用 ActiveX 控制項的應用程式時，請注意下列考量：  
  
-   **安全性** Common Language Runtime 已增強程式碼存取安全性。 具備 Windows Forms 的應用程式可以在完全信任的環境中執行而不發生問題，而在半受信任的環境中則可以存取大部分的功能。 Windows Forms 控制項可以裝載在瀏覽器中，而且不會很複雜。 不過，Windows Forms 上的 ActiveX 控制項無法利用這些安全性加強功能。 執行 ActiveX 控制項需要 unmanaged 程式碼權限，這會使用設定<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType>屬性。 如需有關安全性和 unmanaged 程式碼權限的詳細資訊，請參閱<xref:System.Security.Permissions.SecurityPermissionAttribute>。  
  
-   新增至 Windows Forms 的**擁有權總成本** ActiveX 控制項會與該 Windows Forms 一起完整部署，這樣會大幅增加所建立檔案的大小。 此外，在 Windows Forms 上使用 ActiveX 控制項需要寫入至登錄。 這與不需要這麼做的 Windows Forms 控制項比起來，更容易擴散到使用者的電腦。  
  
    > [!NOTE]
    >  使用 ActiveX 控制項需要使用 COM Interop 包裝函式。 如需詳細資訊，請參閱 [Visual Basic 和 C# 中的 COM 互通性](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
    > [!NOTE]
    >  如果 ActiveX 控制項的成員名稱符合已定義的名稱[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]，然後將 ActiveX 控制項匯入工具會在成員名稱前面加**Ctl**當它建立<xref:System.Windows.Forms.AxHost>衍生的類別。 例如，如果您的 ActiveX 控制項有一個名為 **Layout** 的成員，它在 AxHost 衍生類別中就會被重新命名為 **CtlLayout**，因為 **Layout** 事件是在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中定義的。  
  
## <a name="see-also"></a>另請參閱
- [如何：將 ActiveX 控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)
- [程式碼存取安全性](../../../../docs/framework/misc/code-access-security.md)
- [比較各種語言和程式庫的控制項與可以透過程式設計的物件](https://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)
- [將控制項加入 Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
- [Windows Forms 控制項](../../../../docs/framework/winforms/controls/index.md)
