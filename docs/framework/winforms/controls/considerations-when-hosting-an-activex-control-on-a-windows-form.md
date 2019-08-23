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
ms.openlocfilehash: 0b95bab20299b966b9f3c6e6ce089a641670f974
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933420"
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a>在 Windows Form 上裝載 ActiveX 控制項的考慮因素
雖然 Windows Forms 已進行最佳化來裝載 Windows Forms 控制項，但是您仍然可以使用 ActiveX 控制項。 規劃使用 ActiveX 控制項的應用程式時，請注意下列考量：  
  
- **安全性** Common Language Runtime 已增強程式碼存取安全性。 具備 Windows Forms 的應用程式可以在完全信任的環境中執行而不發生問題，而在半受信任的環境中則可以存取大部分的功能。 Windows Forms 控制項可以裝載在瀏覽器中，而且不會很複雜。 不過，Windows Forms 上的 ActiveX 控制項無法利用這些安全性加強功能。 執行 ActiveX 控制項需要非受控程式碼許可權, 這是使用<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType>屬性所設定的。 如需安全性和非受控碼許可權的詳細資訊<xref:System.Security.Permissions.SecurityPermissionAttribute>, 請參閱。  
  
- 新增至 Windows Forms 的**擁有權總成本** ActiveX 控制項會與該 Windows Forms 一起完整部署，這樣會大幅增加所建立檔案的大小。 此外，在 Windows Forms 上使用 ActiveX 控制項需要寫入至登錄。 這與不需要這麼做的 Windows Forms 控制項比起來，更容易擴散到使用者的電腦。  
  
    > [!NOTE]
    > 使用 ActiveX 控制項需要使用 COM Interop 包裝函式。 如需詳細資訊，請參閱 [Visual Basic 和 C# 中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
    > [!NOTE]
    > 如果 activex 控制項的成員名稱符合在 .NET Framework 中定義的名稱, 則 activex 控制項匯入工具在建立<xref:System.Windows.Forms.AxHost>衍生類別時, 會在成員名稱前面加上**Ctl** 。 例如, 如果您的 ActiveX 控制項具有名為**Layout**的成員, 它會在 AxHost 衍生類別中重新命名為**CtlLayout** , 因為配置事件會在 .NET Framework 內定義。  
  
## <a name="see-also"></a>另請參閱

- [如何：將 ActiveX 控制項新增至 Windows Forms](how-to-add-activex-controls-to-windows-forms.md)
- [程式碼存取安全性](../../misc/code-access-security.md)
- [比較各種語言和程式庫的控制項與可以透過程式設計的物件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [將控制項加入 Windows Forms](putting-controls-on-windows-forms.md)
- [Windows Forms 控制項](index.md)
