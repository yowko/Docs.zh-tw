---
title: 隔離儲存區
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data storage using isolated storage
- stores
- storing data using isolated storage
- isolated storage
- location of isolated storage in file system
- standardizing storage systems
- storing data using isolated storage, when not to use
- code, isolated storage
- isolated storage, options
- data storage using isolated storage, when not to use
- storing data using isolated storage, options
- isolated storage, when not to use
- data storage using isolated storage, options
- isolation
ms.assetid: aff939d7-9e49-46f2-a8cd-938d3020e94e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ab12ac28728535c3bc984d6b37d82f5bf371ba2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isolated-storage"></a>隔離儲存區
<a name="top"></a>對於[!INCLUDE[desktop_appname](../../../includes/desktop-appname-md.md)]應用程式而言，隔離儲存區為資料儲存機制，藉著定義標準化方式，將程式碼與儲存的資料產生關聯，以提供隔離和安全。 標準化也提供其他利益。 系統管理員可以使用設計來操作隔離儲存區的工具，設定檔案存放空間、設定安全性原則，和刪除未使用的資料。 有了隔離儲存區，您的程式碼不再需要唯一路徑去指定檔案系統中的安全位置，並且資料也被保護以免受到只擁有隔離儲存區存取權的其他應用程式的影響。 指示應用程式之存放區域所在位置的硬式編碼資訊是沒有必要的。  
  
> [!IMPORTANT]
>  [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式無法使用隔離儲存區。 請改用 `Windows.Storage` 應用程式開發介面內含的 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 命名空間中的應用程式資料類別來儲存本機資料和檔案。 如需詳細資訊，請參閱 Windows 開發人員中心的 [應用程式資料](/previous-versions/windows/apps/hh464917(v=win.10)) 。  
  
 此主題包括下列章節：  
  
-   [資料區間和存放區](#data_compartments_and_stores)  
  
-   [隔離儲存區的配額](#quotas)  
  
-   [安全存取](#secure_access)  
  
-   [容許的用法和安全性風險](#allowed_usage)  
  
-   [隔離儲存區位置](#isolated_storage_locations)  
  
-   [建立、列舉和刪除隔離儲存區](#isolated_storage_tasks)  
  
-   [隔離儲存區的案例](#scenarios_for_isolated_storage)  
  
-   [相關主題](#related_topics)  
  
-   [參考資料](#reference)  
  
<a name="data_compartments_and_stores"></a>   
## <a name="data-compartments-and-stores"></a>資料區間和存放區  
 當應用程式在檔案中儲存資料時，您必須小心選擇檔案名稱和儲存位置，將儲存位置為另一個應用程式知悉因而遭受損毀的可能性降至最低。 若沒有一個標準系統從中管理這些問題，開發臨機操作技術以使儲存衝突降至最低可能會很複雜，而且結果也不可靠。  
  
 有了隔離儲存區，資料永遠按照使用者和按照組件 (Assembly) 來隔離。 認證 (例如組件的來源或強式名稱) 會決定組件的識別 (Identity)。 資料也可以使用類似的認證，依據應用程式定義域來隔離。  
  
 使用隔離儲存區時，應用程式會將資料儲存至與程式碼識別在某種程度上相關聯的唯一資料區間，例如它的發行者或簽章。 資料區間為抽象概念，不是特定儲存位置；它由一個或多個稱為存放區的隔離儲存區檔案 (包含資料儲存的實際目錄位置) 所構成。 例如，應用程式可能具有與它相關的資料區間，而檔案系統中的目錄則將實作實際保留那個應用程式資料的存放區。 儲存在存放區中的資料可以是任何種類的資料，從使用者的喜好資訊至應用程式的狀態。 對於開發人員而言，資料區間的位置顯而易見。 存放區通常位於用戶端上，不過，伺服器應用程式可以模擬執行操作的使用者，使用隔離儲存區儲存資訊。 隔離儲存區 (Isolated Storage) 也可以配合使用者漫遊設定檔在伺服器上儲存資訊，讓漫遊使用者隨時隨地都能使用資訊。  
  
  
<a name="quotas"></a>   
## <a name="quotas-for-isolated-storage"></a>隔離儲存區的配額  
 配額是對於可用的隔離儲存區數量的限制。 配額包括檔案空間的位元組和目錄相關的負荷以及存放區中的其他資訊。 隔離儲存區使用權限配額，也就是使用 <xref:System.Security.Permissions.IsolatedStoragePermission> 物件設定的儲存區限制。 如果您嘗試寫入的資料超過配額，就會擲回 <xref:System.IO.IsolatedStorage.IsolatedStorageException> 例外狀況。  安全性原則會決定授與程式碼的權限，您可以使用 .NET Framework 組態工具 (Mscorcfg.msc) 修改安全性原則。 已具有 <xref:System.Security.Permissions.IsolatedStoragePermission> 的程式碼僅限使用不超過 <xref:System.Security.Permissions.IsolatedStoragePermission.UserQuota%2A> 屬性所允許的儲存區。 然而，因為程式碼可以提出不同的使用者識別來略過使用權限配額，使用權限配額可充當對程式碼應該如何動作的指導方針，並非做為程式碼行為的固定限制。  
  
 配額並不對漫遊存放區做限制。 因為這點，程式碼需要稍高等級的使用權限來使用它們。 列舉值 <xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByRoamingUser> 和 <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByRoamingUser> 會為漫遊使用者指定使用隔離儲存區的權限。  
  
  
<a name="secure_access"></a>   
## <a name="secure-access"></a>安全存取  
 隔離儲存區的使用讓部分受信任的應用程式能夠藉由電腦的安全性原則所控制的方式來儲存資料。 這對於使用者可能要小心翼翼執行的下載元件特別有用。 當您使用標準 I/O 機制存取檔案系統時，安全性原則很少授與這類程式碼權限。 不過，根據預設，從本機電腦、區域網路或網際網路執行的程式碼將被授與使用隔離儲存區的權限。  
  
 系統管理員可以根據適當的信任等級，限制應用程式或使用者可使用多少隔離儲存區。 此外，系統管理員可以完全移除使用者的保存資料。 若要建立或存取隔離儲存區，程式碼必須具備適當的 <xref:System.Security.Permissions.IsolatedStorageFilePermission> 權限。  
  
 若要存取隔離儲存區，程式碼必須擁有所有必要的原生 (Native) 平台作業系統權限。 例如，必須遵循控制哪些使用者有權使用檔案系統的存取控制清單 (ACL)。 .NET Framework 應用程式已經擁有作業系統權限以存取隔離儲存區，除非它們執行 (平台特定) 模擬。 在這個狀況中，應用程式有責任確保模擬的使用者識別具有適當的作業系統權限，以存取隔離儲存區。 這個存取對於從 Web 執行或下載的程式碼提供便利的方式，以讀取和寫入與特定使用者有關的存放區域。  
  
 通用語言執行平台會使用 <xref:System.Security.Permissions.IsolatedStorageFilePermission> 物件控制對隔離儲存區的存取。 每個物件都有指定下列值的屬性：  
  
-   容許的使用方式，表示允許的存取類型。 這些值為 <xref:System.Security.Permissions.IsolatedStorageContainment> 列舉類型的成員。 如需有關這些值的詳細資訊，請參閱下一節中的表格。  
  
-   儲存區配額，如上一節中所討論。  
  
 在程式碼第一次嘗試開啟存放區時，執行階段要求必須有 <xref:System.Security.Permissions.IsolatedStorageFilePermission> 權限。 它會根據信任程式碼的程度，決定是否要授與這項權限。 如果授與權限，容許的用法和儲存區配額值會由安全性原則和程式碼對 <xref:System.Security.Permissions.IsolatedStorageFilePermission>的要求決定。 安全性原則是使用 .NET Framework 組態工具 (Mscorcfg.msc) 所設定。 要檢查呼叫堆疊中的所有呼叫端，以確保各個呼叫端都至少有適當的允許使用方式。 執行階段也檢查加諸於程式碼 (其已開啟或建立將要儲存檔案的存放區) 的配額。 如果這些條件滿足，即授與使用權限。 每當檔案寫入存放區時，會再度檢查配額。  
  
 要求權限時不需要應用程式程式碼，因為通用語言執行平台根據安全性原則授與適當的 <xref:System.Security.Permissions.IsolatedStorageFilePermission> 。 不過，有時候要求應用程式所需的特定權限 (包括 <xref:System.Security.Permissions.IsolatedStorageFilePermission>) 有其合理原因。  
  
  
<a name="allowed_usage"></a>   
## <a name="allowed-usage-and-security-risks"></a>容許的用法和安全性風險  
 <xref:System.Security.Permissions.IsolatedStorageFilePermission> 所指定的容許用法將決定允許程式碼建立和使用隔離儲存區的程度。 下表顯示如何在對應隔離類型的使用權限中指定容許的使用方式，並摘要各個允許使用方式相關的安全性風險。  
  
|容許的使用方式|隔離類型|安全性影響|  
|-------------------|---------------------|---------------------|  
|<xref:System.Security.Permissions.IsolatedStorageContainment.None>|不允許使用隔離儲存區。|沒有安全性影響。|  
|<xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser>|依據使用者、定義域和組件的隔離。 各個組件在定義域中具有分別的子存放區。 電腦也會隱含隔離使用這項權限的存放區。|這個使用權限等級開放資源給未經授權的過度使用，即使強制的配額對此增加了一些難度。 這被稱為拒絕服務的攻擊。|  
|<xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByRoamingUser>|與 `DomainIsolationByUser`相同，但存放區儲存至將漫遊的位置，如果啟用漫遊使用者設定檔而未限制配額的話。|因為配額必須停用，儲存資源將更容易受到拒絕服務的攻擊傷害。|  
|<xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByUser>|依據使用者和組件的隔離。 電腦也會隱含隔離使用這項權限的存放區。|配額被強制在這個等級，幫助防止拒絕服務的攻擊。 另一個定義域中的相同組件可以存取這個存放區，開啟資訊可在應用程式之間洩漏的可能性。|  
|<xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByRoamingUser>|與 `AssemblyIsolationByUser`相同，但存放區儲存至將漫遊的位置，如果啟用漫遊使用者設定檔而未限制配額的話。|與 `AssemblyIsolationByUser`中相同，但沒有配額，遭到拒絕服務攻擊的風險增加。|  
|<xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>|依據使用者的隔離。 基本上，只有管理的或偵錯的工具使用這個等級的使用權限。|這個使用權限的存取允許程式碼檢視或刪除使用者的任何隔離儲存區檔案或目錄 (不管組件隔離)。 風險包括資訊洩漏和資料遺失 (但不僅限於此)。|  
|<xref:System.Security.Permissions.IsolatedStorageContainment.UnrestrictedIsolatedStorage>|依據所有使用者、定義域和組件的隔離。 基本上，只有管理的或偵錯的工具使用這個等級的使用權限。|這個使用權限將產生完全洩露所有使用者的全部隔離存放區的可能性。|  
  
  
<a name="isolated_storage_locations"></a>   
## <a name="isolated-storage-locations"></a>隔離儲存區位置  
 有時候，使用作業系統的檔案系統來驗證隔離儲存區的變更，很有用處。 您可能也想要知道隔離儲存區檔案的位置。 這個位置依作業系統而不同。 下表顯示在幾個一般作業系統上建立隔離儲存區所在的根 (Root) 位置。 尋找這個根位置下的 Microsoft\IsolatedStorage 目錄。 您必須變更資料夾設定值來顯示隱藏的檔案和資料夾，以便可以在檔案系統中看到隔離儲存區。  
  
|作業系統|檔案系統中的位置|  
|----------------------|-----------------------------|  
|Windows 2000、Windows XP、Windows Server 2003 (從 Windows NT 4.0 升級)|啟用漫遊的存放區 =<br /><br /> \<SYSTEMROOT>\Profiles\\<user\>\Application Data<br /><br /> 非漫遊存放區 =<br /><br /> \<SYSTEMROOT>\Profiles\\<user\>\Local Settings\Application Data|  
|Windows 2000 - 全新安裝 (以及從 Windows 98 和 Windows NT 3.51 升級)|啟用漫遊的存放區 =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings\\<user\>\Application Data<br /><br /> 非漫遊存放區 =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings\\<user\>\Local Settings\Application Data|  
|Windows XP、Windows Server 2003 - 全新安裝 (以及從 Windows 2000 和 Windows 98 升級)|啟用漫遊的存放區 =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings\\<user\>\Application Data<br /><br /> 非漫遊存放區 =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings\\<user\>\Local Settings\Application Data|  
|[!INCLUDE[win8](../../../includes/win8-md.md)]、Windows 7、Windows Server 2008、Windows Vista|啟用漫遊的存放區 =<br /><br /> \<SYSTEMDRIVE>\Users\\<user\>\AppData\Roaming<br /><br /> 非漫遊存放區 =<br /><br /> \<SYSTEMDRIVE>\Users\\<user\>\AppData\Local|  
  
  
<a name="isolated_storage_tasks"></a>   
## <a name="creating-enumerating-and-deleting-isolated-storage"></a>建立、列舉和刪除隔離儲存區  
 .NET Framework 提供 <xref:System.IO.IsolatedStorage> 命名空間中的三個類別，可協助您執行包含隔離儲存區的工作：  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 衍生自 <xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType>，並提供儲存的組件和應用程式檔案的基本管理。 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 類別的執行個體代表位於檔案系統中的單一存放區。  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> 衍生自 <xref:System.IO.FileStream?displayProperty=nameWithType>，並提供對存放區中檔案的存取。  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageScope> 為列舉類型，讓您能夠建立和選取適當隔離類型的存放區。  
  
 隔離儲存區類別允許您建立、列舉和刪除隔離儲存區。 您可以透過 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 物件使用執行這些工作的方法。 某些作業會要求您擁有代表管理隔離儲存區權限的 <xref:System.Security.Permissions.IsolatedStorageFilePermission> 權限，您可能也需要擁有作業系統權限才能存取檔案或目錄。  
  
 如需示範常見隔離儲存區工作的一系列範例，請參閱[相關主題](#related_topics)中所列的「如何」主題。  
  
  
<a name="scenarios_for_isolated_storage"></a>   
## <a name="scenarios-for-isolated-storage"></a>隔離儲存區的案例  
 在許多情況下隔離儲存區非常實用，包括下列四種情境：  
  
-   下載的控制項。 從網際網路下載的 Managed 程式碼控制項不允許透過一般 I/O 類別寫入硬碟，但它們可以使用隔離儲存區保存 (Persist) 使用者的設定值和應用程式狀態。  
  
-   共用的元件儲存區。 應用程式之間共用的元件可以使用隔離儲存區以提供對資料存放區的控制存取。  
  
-   伺服器儲存區。 伺服器應用程式可以使用隔離儲存區，提供個別存放區給向應用程式產生要求的大量使用者。 因為隔離儲存區一直根據使用者來分離，伺服器必須模擬提出要求的使用者。 在這個狀況中，資料是根據主體的識別 (應用程式用以區別其使用者的相同識別) 來隔離。  
  
-   漫遊。 應用程式也可以根據漫遊使用者設定檔來使用隔離儲存區。 這允許使用者的隔離存放區隨著設定檔而漫遊。  
  
 下列情況下不應該使用隔離儲存區：  
  
-   存放具高度價值的機密，例如未加密的金鑰或密碼，因為隔離儲存區不能防範高度信任的程式碼、Unmanaged 程式碼或電腦的信任使用者。  
  
-   儲存程式碼。  
  
-   儲存系統管理員所控制的組態和部署設定。 (使用者喜好不算是組態設定，因為系統管理員並不控制它們)。  
  
 許多應用程式使用資料庫來儲存並隔離資料，這種情況下，資料庫中可能有一個或多個資料列代表特定使用者的儲存區。 當使用者數目還小、使用資料庫的耗用很重大，或沒有資料庫設備存在時，您可以選擇使用隔離儲存區代替資料庫。 同樣，當應用程式需要較資料庫資料列所提供更為彈性和複雜的儲存區時，隔離儲存區可以提供可行的替代方案。  
  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[隔離的類型](../../../docs/standard/io/types-of-isolation.md)|描述各種類型的隔離。|  
|[操作說明：取得隔離儲存區的存放區](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)|提供使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 類別的範例，示範如何使用它來取得使用者和組件所隔離的存放區。|  
|[操作說明：列舉隔離儲存區的存放區](../../../docs/standard/io/how-to-enumerate-stores-for-isolated-storage.md)|示範如何使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> 方法來計算使用者之所有隔離儲存區的大小。|  
|[如何：刪除隔離儲存區中的存放區](../../../docs/standard/io/how-to-delete-stores-in-isolated-storage.md)|示範如何使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A?displayProperty=nameWithType> 方法，以兩種不同的方式刪除隔離存放區。|  
|[操作說明：預期隔離儲存區發生空間不足的情況](../../../docs/standard/io/how-to-anticipate-out-of-space-conditions-with-isolated-storage.md)|示範如何測量隔離存放區內的剩餘空間。|  
|[如何：在隔離儲存區中建立檔案和目錄](../../../docs/standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|提供一些在隔離存放區中建立檔案和目錄的範例。|  
|[如何：尋找隔離儲存區中的現有檔案和目錄](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|示範如何在隔離儲存區中讀取目錄結構和檔案。|  
|[如何：讀取和寫入隔離儲存區中的檔案](../../../docs/standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|提供將字串寫入至隔離儲存區檔案並將它讀回的範例。|  
|[如何：刪除隔離儲存區中的檔案和目錄](../../../docs/standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|示範如何刪除隔離儲存區的檔案和目錄。|  
|[檔案和資料流 I/O](../../../docs/standard/io/index.md)|說明如何執行同步和非同步檔案及資料流存取。|  
  
<a name="reference"></a>   
## <a name="reference"></a>參考資料  
 <xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType>  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream?displayProperty=nameWithType>  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope?displayProperty=nameWithType>
