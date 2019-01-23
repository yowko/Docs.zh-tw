---
title: HOW TO：建立應用程式設定
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
ms.openlocfilehash: ac89851ce9c655ebef3acf2d55ef6659815ca4c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558952"
---
# <a name="how-to-create-application-settings"></a>HOW TO：建立應用程式設定
您可以使用 Managed 程式碼來建立新的應用程式設定，並將設定繫結至表單或表單控制項的屬性，以便在執行階段自動載入及儲存這些設定。  
  
 在下列程序中，您將手動建立一個衍生自 <xref:System.Configuration.ApplicationSettingsBase> 的包裝函式類別。 針對這個類別，您會加入可公開存取的屬性，以代表要公開的每一個應用程式設定。  
  
 您也可以在 Visual Studio 設計工具中，使用最少的程式碼來執行這個程序。  另請參閱[How to:建立使用設計工具的應用程式設定](https://msdn.microsoft.com/library/wabtadw6\(v=vs.110\))。  
  
### <a name="to-create-new-application-settings-programmatically"></a>以程式設計方式建立新的應用程式設定  
  
1.  將新類別加入您的專案中，並且重新命名。 此程序中，我們會呼叫這個類別`MyUserSettings`。 變更類別定義，使該類別衍生自 <xref:System.Configuration.ApplicationSettingsBase>。  
  
2.  在包裝函式類別上為每一個所需的應用程式設定定義屬性，並且依據設定的範圍使用 <xref:System.Configuration.ApplicationScopedSettingAttribute> 或 <xref:System.Configuration.UserScopedSettingAttribute> 來套用該屬性。 如需有關設定範圍的詳細資訊，請參閱 <<c0> [ 應用程式設定概觀](../../../../docs/framework/winforms/advanced/application-settings-overview.md)。 現在，您的程式碼應該如下所示：  
  
     [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  在應用程式中建立這個包裝函式類別的執行個體。 這個執行個體通常會是主要表單的私用成員。 定義類別之後，您需要將類別繫結至屬性；在本例中，即為表單的 <xref:System.Windows.Forms.Form.BackColor%2A> 屬性。 您可以在您的表單來完成`Load`事件處理常式。  
  
     [!code-csharp[ApplicationSettings.Create#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  如果您提供在執行階段變更設定的方式，則需要在關閉表單時將使用者的目前設定儲存至磁碟，否則這些變更將會遺失。  
  
     [!code-csharp[ApplicationSettings.Create#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     您現在已成功建立新的應用程式設定，並將設定繫結至指定的屬性。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 預設的設定提供者 <xref:System.Configuration.LocalFileSettingsProvider> 將資訊以純文字格式保存於組態檔。 這會將安全性限定為目前使用者之作業系統所提供的檔案存取安全性。 因此，您必須小心使用儲存在組態檔中的資訊。 例如，應用程式設定的常見用途之一，是儲存指向應用程式資料存放區的連接字串。 不過，基於安全性考量，這類字串不應包含密碼。 如需連接字串的詳細資訊，請參閱 <xref:System.Configuration.SpecialSetting>。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Configuration.SpecialSettingAttribute>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [應用程式設定概觀](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
- [如何：驗證應用程式設定](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)
