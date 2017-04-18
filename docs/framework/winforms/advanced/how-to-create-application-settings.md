---
title: "如何：建立應用程式設定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "應用程式設定, 建立"
  - "應用程式設定, Windows Form"
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：建立應用程式設定
您可以使用 Managed 程式碼來建立新的應用程式設定，並將設定繫結至表單或表單控制項的屬性，以便在執行階段自動載入及儲存這些設定。  
  
 在下列程序中，您將手動建立一個衍生自 <xref:System.Configuration.ApplicationSettingsBase> 的包裝函式類別。  針對這個類別，您會加入可公開存取的屬性，以代表要公開的每一個應用程式設定。  
  
 您也可以在 Visual Studio 設計工具中，使用最少的程式碼來執行這個程序。  另請參閱[如何：使用設計工具建立應用程式設定](http://msdn.microsoft.com/library/wabtadw6%20\(v=vs.110\))。  
  
### 以程式設計方式建立新的應用程式設定  
  
1.  將新類別加入您的專案中，並且重新命名。  在這個程序中，我們將呼叫  `MyUserSettings` 類別。  變更類別定義，使該類別衍生自 <xref:System.Configuration.ApplicationSettingsBase>。  
  
2.  在包裝函式類別上為每一個所需的應用程式設定定義屬性，並且依據設定的範圍使用 <xref:System.Configuration.ApplicationScopedSettingAttribute> 或 <xref:System.Configuration.UserScopedSettingAttribute> 來套用該屬性。  如需設定範圍的詳細資訊，請參閱[應用程式設定概觀](../../../../docs/framework/winforms/advanced/application-settings-overview.md)。  現在，您的程式碼應該如下所示：  
  
     [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  在應用程式中建立這個包裝函式類別的執行個體。  這個執行個體通常會是主要表單的私用成員。  定義類別之後，您需要將類別繫結至屬性；在本例中，即為表單的 <xref:System.Windows.Forms.Form.BackColor%2A> 屬性。  您可以在表單的  `Load`  事件處理常式中完成這個動作。  
  
     [!code-csharp[ApplicationSettings.Create#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  如果您提供在執行階段變更設定的方式，則需要在關閉表單時將使用者的目前設定儲存至磁碟，否則這些變更將會遺失。  
  
     [!code-csharp[ApplicationSettings.Create#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     您現在已成功建立新的應用程式設定，並將設定繫結至指定的屬性。  
  
## .NET Framework 安全性  
 預設的設定提供者 <xref:System.Configuration.LocalFileSettingsProvider> 將資訊以純文字格式保存於組態檔。  這會將安全性限定為目前使用者之作業系統所提供的檔案存取安全性。  因此，您必須小心使用儲存在組態檔中的資訊。  例如，應用程式設定的常見用途之一，是儲存指向應用程式資料存放區的連接字串。  不過，基於安全性考量，這類字串不應包含密碼。  如需連接字串的詳細資訊，請參閱 <xref:System.Configuration.SpecialSetting>。  
  
## 請參閱  
 <xref:System.Configuration.SpecialSettingAttribute>   
 <xref:System.Configuration.LocalFileSettingsProvider>   
 [應用程式設定概觀](../../../../docs/framework/winforms/advanced/application-settings-overview.md)   
 [如何：驗證應用程式設定](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)