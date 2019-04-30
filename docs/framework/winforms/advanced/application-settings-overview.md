---
title: 應用程式設定概觀
ms.date: 03/30/2017
f1_keywords:
- ApplicationsSettingsOverview
helpviewer_keywords:
- application settings [Windows Forms], about application settings
- dynamic properties
- user preferences [Windows Forms], tracking
ms.assetid: 0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc
ms.openlocfilehash: b603e81a342652a6639f54a78fb998cda5fdc35a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972415"
---
# <a name="application-settings-overview"></a>應用程式設定概觀
本主題討論如何代表您的應用程式和使用者來建立及儲存設定資料。  
  
 Windows Form 應用程式設定功能可讓您輕鬆地建立、儲存和維護自訂應用程式和用戶端電腦上的使用者喜好設定。 利用 Windows Form 應用程式設定，您不只可以儲存應用程式資料，例如資料庫連接字串，也可以儲存使用者專屬資料，例如使用者應用程式喜好設定。 使用 Visual Studio 或自訂的 Managed 程式碼，您可以建立新的設定、從磁碟讀取及寫入磁碟、將其繫結至您表單上的屬性，並驗證載入和儲存之前的設定資料。  
  
 應用程式設定可讓開發人員使用極少的自訂程式碼在應用程式中儲存狀態，可取代舊版 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]中的動態屬性。 透過唯讀的晚期繫結動態屬性，應用程式設定包含許多改良，而且需要更多的自訂程式設計。 動態屬性類別已保留在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]，但它們只是精簡包裝應用程式設定類別的殼層類別。  
  
## <a name="what-are-application-settings"></a>什麼是應用程式設定？  
 Windows Form 應用程式通常需要這些對於執行應用程式很重要的資料，但您不想直接在應用程式的程式碼中包含這些資料。 如果您的應用程式使用 Web 服務或資料庫伺服器，您可能要將此資訊儲存在不同的檔案，以便您在未來可變更它而不需重新編譯。 同樣地，您的應用程式可能需要儲存目前使用者的特定資料。 例如，大部分的應用程式有能自訂應用程式外觀和行為的使用者喜好設定。  
  
 以應用程式設定解決此兩項需求，要提供在用戶端電腦上於應用程式範圍和使用者範圍設定的簡單儲存方法。 您可使用 Visual Studio 或程式碼編輯器，藉由指定其名稱、資料類型及範圍 (應用程式或使用者) 來定義指定屬性的設定。 您甚至可以將相關的設定置於具名群組，以便更容易地使用並提升可讀性。 一旦定義好之後，這些設定會在執行階段自動保存並讀回記憶體。 可外掛式架構可變更持續性機制，但根據預設，會使用本機檔案系統。  
  
 應用程式設定的運作方式是以 XML 保存資料到不同的組態 (.config)，這與此設定為應用程式範圍或使用者範圍相對應。 在大部分情況下，應用程式範圍的設定都是唯讀的；因為它們是程式的資訊，您通常不需要覆寫它們。 相較之下，在執行階段可以讀取和寫入使用者範圍的設定，即使您的應用程式在部分信任下執行。 如需部分信任的詳細資訊，請參閱 [Security in Windows Forms Overview](../security-in-windows-forms-overview.md)。  
  
 設定會在組態檔中儲存為 XML 片段。 應用程式範圍的設定由 `<application.Settings>` 項目代表，且通常會放在 *app*.exe.config，其中 *app* 是您主要可執行檔的名稱。 使用者範圍的設定由 `<userSettings>` 項目代表，放在 *user*.config，其中 *user* 是目前正在執行應用程式之人員的使用者名稱。 您必須根據應用程式部署 *app*.exe.config 檔案；該設定架構將會依應用程式第一次儲存該使用者設定的需要來建立 *user*.config 檔案。 您也可以在 `<userSettings>` app *.exe.config 中定義*區塊，以提供使用者範圍設定的預設值。  
  
 自訂控制項也可以藉由實作 <xref:System.Configuration.IPersistComponentSettings> 介面來儲存自己的設定，這介面會公開 <xref:System.Configuration.IPersistComponentSettings.SaveSettings%2A> 方法。 Windows Form <xref:System.Windows.Forms.ToolStrip> 控制項實作此介面，以便儲存應用程式工作階段之間工具列和工具列項目的位置。 如需自訂控制項和應用程式設定的詳細資訊，請參閱[自訂控制項的應用程式設定](application-settings-for-custom-controls.md)。  
  
## <a name="limitations-of-application-settings"></a>應用程式設定的限制  
 您無法在裝載 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]的 Unmanaged 應用程式使用應用程式設定。 設定將不會在這類環境中運作，如 Visual Studio 增益集、Microsoft Office 的 C++ 及裝載於 Internet Explorer 或 Microsoft Outlook 增益集及專案中的控制項。  
  
 您目前無法在 Windows Form 中繫結某些屬性。 最值得注意的範例是 <xref:System.Windows.Forms.Form.ClientSize%2A> 屬性，因為繫結至這個屬性會在執行階段造成無法預期的行為。 通常您可以程式設計的方式儲存並載入這些設定，來解決這些問題。  
  
 應用程式設定並沒有內建自動加密資訊的能力。 您絕不應該以純文字格式儲存安全性相關的資訊，例如資料庫密碼。 如果您想要儲存這類的機密資訊，身為應用程式開發人員，您要負責確保安全。 如果您想要儲存連接字串，我們建議您使用 Windows Integrated Security，並且不要求助於硬式編碼成 URL 的密碼。 如需詳細資訊，請參閱 [Code Access Security and ADO.NET](../../data/adonet/code-access-security.md)。  
  
## <a name="getting-started-with-application-settings"></a>開始使用應用程式設定  
 如果您使用 Visual Studio，您可以在 Windows Form 設計工具中使用 [屬性]  視窗中的 **(ApplicationSettings)** 屬性定義設定。 當您以這種方式定義設定時，Visual Studio 會自動建立自訂的 Managed 包裝函式類別，這會以類別屬性與每個設定產生關聯。 Visual Studio 也會負責將設定繫結到表單或控制項上的屬性，以便於在表單顯示時自動還原控制項設定，以及在表單關閉時會自動儲存控制項設定。  
  
 如果您想要更進一步控制您的設定，您可以定義自己的自訂應用程式設定包裝函式類別。 這可以藉由衍生自 <xref:System.Configuration.ApplicationSettingsBase>的類別來完成，以及藉由加入對應至每個設定的屬性，並將特殊屬性套用至這些屬性。 如需有關建立包裝函式類別的詳細資訊，請參閱[應用程式設定架構](application-settings-architecture.md)。  
  
 您也可以使用 <xref:System.Windows.Forms.Binding> 類別以程式設計的方式來繫結設定至表單和控制項上的屬性。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- <xref:System.Configuration.IPersistComponentSettings>
- [如何：驗證應用程式設定](how-to-validate-application-settings.md)
- [管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
- [如何：在執行階段使用的讀取設定C#](how-to-read-settings-at-run-time-with-csharp.md)
- [使用應用程式設定和使用者設定](using-application-settings-and-user-settings.md)
- [應用程式設定架構](application-settings-architecture.md)
- [Application Settings for Custom Controls](application-settings-for-custom-controls.md)
