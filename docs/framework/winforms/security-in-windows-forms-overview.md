---
title: Windows Form 中的安全性概觀
ms.date: 03/30/2017
helpviewer_keywords:
- code access security [Windows Forms], Windows Forms
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms], about security
- access control [Windows Forms], Windows Forms
ms.assetid: 4810dc9f-ea23-4ce1-8ea1-657f0ff1d820
ms.openlocfilehash: ef90daa9700a60e3d88f75439bf8511b67a71dda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541407"
---
# <a name="security-in-windows-forms-overview"></a>Windows Form 中的安全性概觀
在 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 發行之前，在使用者電腦上執行的所有程式碼，對資源的存取權限都和電腦的使用者相同。 例如，如果使用者可以存取檔案系統，程式碼就可以存取檔案系統，如果使用者可以存取某個資料庫，程式碼就可以存取該資料庫。 就使用者明確安裝在本機電腦上的可執行檔中的程式碼而言，也許這些權限是可接受的，但是就來自網際網路或近端內部網路的潛在惡意程式碼而言，可能就無法接受了。 不應該讓這個程式碼在沒有權限的情況下，存取使用者的電腦資源。  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 引進一種稱為「程式碼存取安全性」的基礎結構，可讓您區分程式碼擁有的權限與使用者擁有的權限。 根據預設，來自網際網路及內部網路的程式碼，只能在所謂部分信任的環境中執行。 部分信任會使應用程式遵守一系列的限制，例如，限制應用程式不能存取本機硬碟，且無法執行 Unmanaged 程式碼等等。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 會依據程式碼的身分識別，控制可允許該程式碼存取的資源；例如，程式碼來自何處、是否有[強式名稱組件](../../../docs/framework/app-domains/strong-named-assemblies.md)、是否已簽署憑證等等。  
  
 您用來部署 Windows Form 應用程式的 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 技術，可協助您更輕鬆地開發可在部分信任、完全信任或提高權限的部分信任中執行的應用程式。 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 提供「提高權限」和「受信任的應用程式部署」之類的功能，讓您的應用程式能夠以負責任的方式，向本機使用者要求完全信任或提高權限。  
  
## <a name="understanding-security-in-the-net-framework"></a>了解 .NET Framework 中的安全性  
 程式碼存取安全性可依據程式碼的來源，以及程式碼其他方面的身分識別，提供程式碼各種程度的信任等級。 如需 Common Language Runtime 用來判斷安全性原則的辨識項相關資訊，請參閱[辨識項](http://msdn.microsoft.com/library/64ceb7c8-a0b4-46c4-97dc-6c22da0539da)。 它可以幫助保護電腦系統不受惡意程式碼的威脅，並幫助防止受信任的程式碼有意或無意地危及安全性。 程式碼存取安全性也讓您更充分掌控您的應用程式可以執行哪些動作，因為您可以只指定您要讓應用程式擁有的那些權限。 程式碼存取安全性會影響以 Common Language Runtime 為目標的所有 Managed 程式碼，即使該程式碼沒有進行單一程式碼存取安全性權限檢查也一樣。 如需 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中安全性的詳細資訊，請參閱[重要的安全性概念](../../../docs/standard/security/key-security-concepts.md)和[程式碼存取安全性基本概念](../../../docs/framework/misc/code-access-security-basics.md)。  
  
 如果使用者不透過 Web 伺服器或檔案共用，而直接執行 Windows Form 可執行檔，則授與應用程式的信任層級，取決於程式碼所在的位置，以及其啟動方式。 當應用程式執行時，會自動受到評估，並且會從 Common Language Runtime 收到具名權限集合。 根據預設，來自本機電腦的程式碼會被授與完全信任權限集合，來自區域網路的程式碼會被授與近端內部網路權限集合，而來自網際網路的程式碼會被授與網際網路權限集合。  
  
> [!NOTE]
>  在 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 1.0 版 Service Pack 1 和 Service Pack 2 中，網際網路區域程式碼群組會收到 Nothing 權限集合。 在 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 的所有其他版本中，網際網路區域程式碼群組都會收到網際網路權限集合。  
>   
>  各權限集合中授與的預設權限詳列於[預設安全性原則](http://msdn.microsoft.com/library/2c086873-0894-4f4d-8f7e-47427c1a3b55)主題中。 根據應用程式接收的權限，它會正確執行，或是產生安全性例外狀況。  
>   
>  許多 Windows Form 應用程式都會使用 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 來部署。 用來產生 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 部署的工具所擁有的安全性預設值不同於先前討論的內容。 如需詳細資訊，請參閱下列討論：  
  
 授與應用程式的實際權限可能不同於預設值，因為安全性原則是可以修改的，這表示您的應用程式可能在某部電腦上具有權限，而在另一部電腦上則沒有。  
  
## <a name="developing-a-more-secure-windows-forms-application"></a>開發更安全的 Windows Form 應用程式  
 在應用程式開發的所有步驟中，安全性都很重要。 一開始請先檢閱並遵循[安全程式碼撰寫方針](../../../docs/standard/security/secure-coding-guidelines.md)。  
  
 接著，決定您的應用程式必須在完全信任中執行，或是應該在部分信任中執行。 以完全信任來執行您的應用程式，比較容易存取本機電腦上的資源，但是如果沒有嚴格遵守＜安全程式碼撰寫方針＞主題來設計及開發您的應用程式，就會讓您的應用程式及其使用者暴露在高度的安全性風險中。 以部分信任來執行您的應用程式，比較容易開發較安全的應用程式，並大幅降低風險，但是需要詳細規劃如何實作特定功能。  
  
 如果您選擇部分信任 (也就是網際網路或近端內部網路權限集合)，請決定您想要讓應用程式如何在此環境中運作。 Windows Form 提供更安全的替代方式，可在非完全信任的環境中實作功能。 針對部分信任和完全信任的環境，都可以用不同方式來設計和撰寫應用程式的某些部分，例如資料存取。 某些 Windows Form 功能 (例如應用程式設定) 是為了在部分信任中運作而設計。 如需詳細資訊，請參閱[應用程式設定概觀](../../../docs/framework/winforms/advanced/application-settings-overview.md)。  
  
 如果您的應用程式所需的權限，超出部分信任的限制，但是您不想要在完全信任中執行，您可以在部分信任中執行，並且只確立您需要的那些額外權限。 例如，如果您想要在部分信任中執行，但必須為您的應用程式授與使用者檔案系統上之目錄的唯讀存取權，您可以只針對該目錄要求 <xref:System.Security.Permissions.FileIOPermission>。 如果正確使用，這種方法可以給予應用程式更多功能，並且讓使用者的安全性風險降到最低。  
  
 當您開發要在部分信任中執行的應用程式時，請追蹤應用程式必須執行的權限，以及應用程式可以選擇性使用的權限。 在已知所有權限的情況下，您應針對應用程式層級的權限提出宣告式要求。 要求權限時會通知 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 執行階段您的應用程式需要哪些權限，以及明確不想要哪些權限。 如需有關要求權限的詳細資訊，請參閱[要求權限](http://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2)。  
  
 當您要求選擇性權限時，您必須處理當應用程式執行的動作需要未被授與的權限時，所產生的安全性例外狀況。 適當處理 <xref:System.Security.SecurityException> 可確保您的應用程式能夠繼續運作。 您的應用程式可以使用例外狀況來判斷是否應該為使用者停用某功能。 例如，如果未授與必要的檔案權限，應用程式可以停用 [儲存] 功能表選項。  
  
 有時候，很難知道您是否已確立所有適當的權限。 比方說，表面上看起來無害的方法呼叫，可能會在其執行期間的某個時間點存取檔案系統。 如果您未以所有的必要權限來部署應用程式，在桌面上偵錯時，測試可能沒問題，但部署時可能會失敗。 這兩個[!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)]SDK 和[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]包含用來計算應用程式所需的權限： MT.exe 可命令列工具及 Visual studio 中，「 計算使用權限 」 功能分別。  
  
 下列主題說明其他 Windows Form 安全性功能。  
  
|主題|描述|  
|-----------|-----------------|  
|-   [Windows Forms 中更安全的檔案和資料存取](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)|說明如何在部分信任的環境中存取檔案和資料。|  
|-   [Windows Forms 中更安全的列印](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)|說明如何在部分信任的環境中存取列印功能。|  
|-   [Windows Forms 中的其他安全性考量](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)|說明如何在部分信任的環境中執行視窗操作、使用剪貼簿，以及呼叫 Unmanaged 程式碼。|  
  
-  
  
### <a name="deploying-an-application-with-the-appropriate-permissions"></a>使用適當的權限部署應用程式  
 將 Windows Form 應用程式部署至用戶端電腦時，最常見的方法是使用 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]，這個部署技術會描述應用程式必須執行的所有元件。 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 使用稱為資訊清單的 XML 檔案來描述構成應用程式的組件和檔案，以及應用程式所需的權限。  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 有兩種技術可在用戶端電腦上要求提高權限。 這兩種技術都需要使用 Authenticode 憑證。 該憑證有助於確保應用程式的使用者是來自受信任的來源。  
  
 下表將描述這些技術。  
  
|提高權限技術|描述|  
|------------------------------------|-----------------|  
|權限提高|在應用程式第一次執行時，會以安全性對話方塊來提示使用者。 [權限提高] 對話方塊會通知使用者是誰發行該應用程式，讓使用者能夠明智地決定是否要授與其額外的信任|  
|受信任的應用程式部署|需要系統管理員在用戶端電腦上執行發行者 Authenticode 憑證的單次安裝。 從此之後，有簽署憑證的任何應用程式都會視為受信任，並且可以在本機電腦上以完全信任執行，而不會有其他提示。|  
  
 您要選擇哪一種技術，將取決於您的部署環境。 如需詳細資訊，請參閱[選擇 ClickOnce 部署策略](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy)。  
  
 根據預設，[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]部署使用 Visual Studio 的應用程式或[!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)]SDK 工具 （Mage.exe 和 MageUI.exe） 設定為具有完全信任的用戶端電腦上執行。 如果您在部署應用程式時，是使用部分信任，或是只有使用某些額外的權限，則必須變更這個預設值。 您可以使用 Visual Studio 或[!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)]SDK 工具 MageUI.exe，當您設定您的部署。 如需有關如何使用 MageUI.exe 的詳細資訊，請參閱＜逐步解說：從命令列部署 ClickOnce 應用程式＞。  另請參閱[如何：設定 ClickOnce 應用程式的自訂權限](http://msdn.microsoft.com/library/hafybdaa\(v=vs.110\))或[如何：設定 ClickOnce 應用程式的自訂權限](http://msdn.microsoft.com/library/hafybdaa\(v=vs.120\))。  
  
 如需有關 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 安全性層面和權限提高的詳細資訊，請參閱[保護 ClickOnce 應用程式](/visualstudio/deployment/securing-clickonce-applications)。 如需有關受信任的應用程式部署的詳細資訊，請參閱[受信任的應用程式部署概觀](/visualstudio/deployment/trusted-application-deployment-overview)。  
  
### <a name="testing-the-application"></a>測試應用程式  
 如果您已經使用 Visual Studio 部署 Windows Forms 應用程式，您可以啟用偵錯部分信任或受限制的使用權限集合從開發環境中。  另請參閱[如何：以限制使用權限偵錯 ClickOnce 應用程式](http://msdn.microsoft.com/library/593zkfdf\(v=vs.110\))或[如何：以限制使用權限偵錯 ClickOnce 應用程式](http://msdn.microsoft.com/library/593zkfdf\(v=vs.120\))。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Forms 安全性](../../../docs/framework/winforms/windows-forms-security.md)  
 [程式碼存取安全性的基本概念](../../../docs/framework/misc/code-access-security-basics.md)  
 [ClickOnce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)  
 [受信任的應用程式部署概觀](/visualstudio/deployment/trusted-application-deployment-overview)  
 [Mage.exe (資訊清單產生和編輯工具)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 [MageUI.exe (圖形用戶端、資訊清單產生和編輯工具)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
