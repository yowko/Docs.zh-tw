---
title: SignTool.exe (簽署工具)
ms.date: 03/30/2017
helpviewer_keywords:
- Sign tool
- SignTool.exe
ms.assetid: 0c25ff6c-bff3-422e-b017-146a3ee86cb9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14207dcefe053e596052c9b94078333c1c714641
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185571"
---
# <a name="signtoolexe-sign-tool"></a>SignTool.exe (簽署工具)
簽署工具是一項命令列工具，會以數位方式簽署檔案、驗證檔案中的簽章以及為檔案加上時間戳記。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
signtool [command] [options] [file_name | ...]  
```  
  
## <a name="parameters"></a>參數  
  
|引數|說明|  
|--------------|-----------------|  
|`command`|四個命令之一 (`catdb`、`sign`、`Timestamp` 或 `Verify`)，指定要對檔案執行的操作。 如需每個命令的描述，請參閱下一個表格。|  
|`options`|修改命令的選項。 除了全域 `/q` 和 `/v` 選項外，每個命令支援一組唯一的選項。|  
|`file_name`|要簽署之檔案的路徑。|  
  
 簽署工具支援下列命令。 每個命令都會搭配一組獨特選項使用，這些選項列於個別區段中。  
  
|命令|說明|  
|-------------|-----------------|  
|`catdb`|在目錄資料庫中加入或移除目錄檔。 目錄資料庫可以用來自動查閱目錄檔，並且是由 GUID 所識別。 如需 `catdb` 命令支援選項的清單，請參閱 [catdb 命令選項](../../../docs/framework/tools/signtool-exe.md#catdb)。|  
|`sign`|數位簽署檔案。 數位簽章可以防止檔案遭到篡改，而且可讓使用者根據簽署憑證確認簽署者。 如需 `sign` 命令支援選項的清單，請參閱 [sign 命令選項](../../../docs/framework/tools/signtool-exe.md#sign)。|  
|`Timestamp`|為檔案加上時間戳記。 如需 `TimeStamp` 命令支援選項的清單，請參閱 [TimeStamp 命令選項](../../../docs/framework/tools/signtool-exe.md#TimeStamp)。|  
|`Verify`|藉由判斷簽署憑證是否由受信任的授權單位所發佈、簽署憑證是否已撤銷，以及簽署憑證是否為特定原則的有效憑證，來驗證檔案的數位簽章。 如需 `Verify` 命令支援選項的清單，請參閱 [Verify 命令選項](../../../docs/framework/tools/signtool-exe.md#Verify)。|  
  
 下列選項適用於所有簽署工具命令。  
  
|Global 選項|說明|  
|-------------------|-----------------|  
|**/q**|如果命令成功執行則不顯示任何輸出，如果命令失敗則顯示最少的輸出。|  
|**/v**|不論命令執行成功或失敗，都顯示詳細資訊輸出，並顯示警告訊息。|  
|**/debug**|顯示偵錯資訊。|  
  
<a name="catdb"></a>   
## <a name="catdb-command-options"></a>catdb 命令選項  
 下表列出可以搭配 `catdb` 命令使用的選項。  
  
|Catdb 選項|說明|  
|------------------|-----------------|  
|`/d`|指示預設目錄資料庫已經更新。 如果未使用 `/d` 和 `/g` 選項，簽署工具就會更新系統元件和驅動程式資料庫。|  
|`/g` *GUID*|指定由全域唯一識別項 *GUID* 所識別的目錄資料庫已更新。|  
|`/r`|從目錄資料庫移除指定的目錄。 如果沒有指定這個選項，簽署工具就會在目錄資料庫中加入指定的目錄。|  
|`/u`|指定為加入的目錄檔自動產生一個唯一的名稱。 必要時，目錄檔會重新命名，以避免與現有的目錄檔發生名稱衝突。 如果沒有指定這個選項，簽署工具會覆寫具有與所要加入之目錄相同名稱的所有現有目錄。|  
  
<a name="sign"></a>   
## <a name="sign-command-options"></a>Sign 命令選項  
 下表列出可以搭配 `sign` 命令使用的選項。  
  
|Sign 命令選項|說明|  
|-------------------------|-----------------|  
|`/a`|自動選取最佳的簽署憑證。 簽署工具會找到滿足所有指定條件的所有有效憑證，並且選取有效時間最長的一個。 如果沒有這個選項，簽署工具只需要找出一個有效的簽署憑證。|  
|`/ac`  *檔案*|從 *file* 將其他憑證加入至簽章區塊。|  
|`/as`|附加這個簽章。 如果主要簽章不存在，則會設定這個簽章做為主要簽章。|  
|`/c`  *CertTemplateName*|指定適用於簽署憑證的「憑證範本名稱」(Certificate Template Name)，這是一個 Microsoft 擴充功能。|  
|`/csp`  *CSPName*|指定包含私密金鑰容器的密碼編譯服務提供者 (Cryptographic Service Provider，CSP)。|  
|`/d`  *Desc*|指定簽署內容的描述。|  
|`/du`  *URL*|為已簽署的內容之擴充描述指定統一資源定位器 (Uniform Resource Locator，URL)。|  
|`/f`  *SignCertFile*|指定檔案中的簽署憑證。 如果檔案為「個人資訊交換」(PFX) 格式並且受密碼保護，請使用 `/p` 選項指定密碼。 如果檔案不包含私密金鑰，請使用 `/csp` 和 `/kc` 選項，以指定 CSP 和私密金鑰容器的名稱。|  
|`/fd`|指定要用於建立檔案簽章的檔案摘要演算法。 預設為 SHA1。|  
|`/i`  *IssuerName*|指定簽署憑證的簽發者名稱。 這個值可以是完整簽發者名稱的子字串。|  
|`/kc`  *PrivKeyContainerName*|指定私密金鑰容器名稱。|  
|`/n`  *SubjectName*|指定簽署憑證的主體名稱。 這個值可以是完整主體名稱的子字串。|  
|`/nph`|如果支援，則隱藏可執行檔的頁面雜湊。 預設取決於 SIGNTOOL_PAGE_HASHES 環境變數和 wintrust.dll 版本。 若為非 PE 檔案，則會忽略這個選項。|  
|`/p`  *密碼*|指定用來開啟 PFX 檔案的密碼  (使用 `/f` 選項指定 PFX 檔)。|  
|`/p7` *路徑*|指定為每個指定內容檔產生公開金鑰加密標準 (PKCS) #7 檔案。 PKCS #7 檔案會命名為*路徑*\\*檔案名稱*.p7。|  
|`/p7ce` *值*|指定已簽署的 PKCS #7 內容的選項。 將 *Value* 設定為 "Embedded" 會將簽署內容內嵌在 PKCS #7 檔案中，設定為 "DetachedSignedData" 會產生已中斷連結的 PKCS #7 檔案的簽署資料部分。 如果未使用 `/p7ce` 選項，則預設會內嵌簽署的內容。|  
|`/p7co` *\<OID>*|指定識別已簽署 PKCS #7 內容的物件識別項 (OID)。|  
|`/ph`|如果支援，則產生可執行檔的頁面雜湊。|  
|`/r`  *RootSubjectName*|指定簽署憑證必須鏈結之根憑證的主體名稱。 這個值可以是完整根憑證主體名稱的子字串。|  
|`/s`  *StoreName*|指定搜尋憑證時要開啟的存放區。 如果沒有指定這個選項，則會開啟 `My` 存放區。|  
|`/sha1`  *Hash*|指定簽署憑證的 SHA1 雜湊。 在多重憑證符合其餘參數指定的準則時，SHA1 雜湊最常被指定。|  
|`/sm`|指定使用電腦存放區，而非使用者存放區。|  
|`/t`  *URL*|指定時間戳記伺服器的 URL。 如果沒有這個選項 (或 `/tr`)，簽署的檔案就不會加上時間戳記。 如果加上時間戳記失敗，便會產生警告。 這個選項無法與 `/tr` 選項搭配使用。|  
|`/td`  *alg*|與 `/tr` 選項一起使用以要求 RFC 3161 時間戳記伺服器使用的摘要演算法。|  
|`/tr`  *URL*|指定 RFC 3161 時間戳記伺服器的 URL。 如果沒有這個選項 (或 `/t`)，簽署的檔案就不會加上時間戳記。 如果加上時間戳記失敗，便會產生警告。 這個選項無法與 `/t` 選項搭配使用。|  
|`/u`  *使用量*|指定在簽署憑證時必須存在的增強金鑰使用方法 (Enhanced Key Usage，EKU)。 使用方法的值可以利用 OID 或字串指定。 預設的使用方法為 "Code Signing" (1.3.6.1.5.5.7.3.3)。|  
|`/uw`|指定「Windows 系統元件驗證」(1.3.6.1.4.1.311.10.3.6) 的使用方式。|  
  
 如需使用方式範例，請參閱[使用 SignTool 簽署檔案](/windows/desktop/SecCrypto/using-signtool-to-sign-a-file)。  
  
<a name="TimeStamp"></a>   
## <a name="timestamp-command-options"></a>TimeStamp 命令選項  
 下表列出可以搭配 `TimeStamp` 命令使用的選項。  
  
|TimeStamp 選項|說明|  
|----------------------|-----------------|  
|`/p7`|為 PKCS #7 檔案加上時間戳記。|  
|`/t`  *URL*|指定時間戳記伺服器的 URL。 要加上時間戳記的檔案必須先經過簽署。 必須有 `/t` 或 `/tr` 任一選項。|  
|`/td`  *alg*|要求 RFC 3161 時間戳記伺服器使用的摘要演算法。 `/td` 可搭配 `/tr` 選項使用。|  
|`/tp` *索引*|在 *index* 的簽章加上時間戳記。|  
|`/tr`  *URL*|指定 RFC 3161 時間戳記伺服器的 URL。 要加上時間戳記的檔案必須先經過簽署。 必須有 `/tr` 或 `/t` 任一選項。|  
  
 如需使用範例，請參閱[新增時間戳記至先前已簽署的檔案](/windows/desktop/SecCrypto/adding-time-stamps-to-previously-signed-files)。  
  
<a name="Verify"></a>   
## <a name="verify-command-options"></a>驗證命令選項  
  
|Verify 選項|說明|  
|-------------------|-----------------|  
|`/a`|指定所有方法都可以用來驗證檔案。 首先會搜尋目錄資料庫，判斷檔案是否已在目錄中簽署。 如果檔案未在任何目錄中簽署，簽署工具便會嘗試驗證檔案的內嵌簽署。 驗證不一定已在目錄中簽署的檔案時，建議您採用這個選項。 這些檔案的範例包括 Windows 檔案或驅動程式。|  
|`/ad`|使用預設目錄資料庫尋找目錄。|  
|`/ag` *CatDBGUID*|在 *CatDBGUID* 所識別的目錄資料庫中尋找目錄。|  
|`/all`|確認在包含多個簽章的檔案中的所有簽章。|  
|`/as`|使用系統元件 (驅動程式) 目錄資料庫尋找目錄。|  
|`/c` *CatFile*|依名稱指定目錄檔。|  
|`/d`|指定簽署工具應列印描述及描述 URL。|  
|`/ds`  *索引*|驗證位於指定位置的簽章。|  
|`/hash` (`SHA1`&#124;`SHA256`)|指定在目錄中搜尋檔案時，要使用的選擇性雜湊演算法。|  
|`/kp`|指定應以核心模式驅動程式簽署原則執行驗證。|  
|`/ms`|使用多個驗證語意。 在 [!INCLUDE[win8](../../../includes/win8-md.md)] 及以上版本上，這是 [WinVerifyTrust](/windows/desktop/api/wintrust/nf-wintrust-winverifytrust) 呼叫的預設行為。|  
|`/o` *版本*|根據作業系統版本驗證檔案。 *Version* 的形式如下：*PlatformID*:*VerMajor*.*VerMinor*.*BuildNumber*。 *PlatformID* 代表 <xref:System.PlatformID> 列舉成員的基礎值。 **重要：** 建議使用 `/o` 參數。 如果未指定 `/o`，SignTool.exe 可能會傳回未預期的結果。 例如，如果您未包含 `/o` 參數，在舊版作業系統上正確驗證的系統目錄，可能無法在較新版作業系統正確驗證。|  
|`/p7`|驗證 PKCS #7 檔案。 PKCS #7 驗證沒有使用任何現有的原則。 檢查簽章，並建置簽署憑證鏈結。|  
|`/pa`|指定使用預設 Authenticode 驗證原則。 如果未指定 `/pa` 選項，簽署工具便會使用「Windows 驅動程式驗證原則」(Windows Driver Verification Policy)。 這個選項無法與 `catdb` 選項搭配使用。|  
|`/pg` *PolicyGUID*|依 GUID 指定驗證原則。 *PolicyGUID* 會對應至驗證原則的 ActionID。 這個選項無法與 `catdb` 選項搭配使用。|  
|`/ph`|指定簽署工具應列印及驗證頁面雜湊值。|  
|`/r` *RootSubjectName*|指定簽署憑證必須鏈結之根憑證的主體名稱。 這個值可以是完整根憑證主體名稱的子字串。|  
|`/tw`|指定如果簽章未加上時間戳記，則應產生警告。|  
  
 如需使用方式範例，請參閱[使用 SignTool 驗證檔案簽章](/windows/desktop/SecCrypto/using-signtool-to-verify-a-file-signature)。  
  
## <a name="return-value"></a>傳回值  
 簽署工具終止時會傳回下列其中一個結束代碼。  
  
|結束代碼|說明|  
|---------------|-----------------|  
|0|執行成功。|  
|1|執行失敗。|  
|2|執行已完成，但出現警告。|  
  
## <a name="examples"></a>範例  
 下列命令會將目錄檔 MyCatalogFileName.cat 加入至系統元件和驅動程式資料庫。 如有必要防止取代名為 `/u` 的現有目錄檔案，`MyCatalogFileName.cat` 選項會產生一個唯一的名稱。  
  
```  
signtool catdb /v /u MyCatalogFileName.cat  
```  
  
 下列命令會使用最佳憑證自動簽署檔案。  
  
```  
signtool sign /a MyFile.exe  
```  
  
 下列命令使用儲存在受密碼保護之 PFX 檔中的憑證存放區，對檔案進行數位簽署。  
  
```  
signtool sign /f MyCert.pfx /p MyPassword MyFile.exe  
```  
  
 下列命令會對檔案進行數位簽署和時間戳記。 用於簽署檔案的憑證存放在 PFX 檔中。  
  
```  
signtool sign /f MyCert.pfx /t http://timestamp.verisign.com/scripts/timstamp.dll MyFile.exe  
```  
  
 下列命令會使用位於主旨名稱為 `My` 之 `My Company Certificate` 存放區中的憑證來簽署檔案。  
  
```  
signtool sign /n "My Company Certificate" MyFile.exe  
```  
  
 下列命令會簽署 ActiveX 控制項，並在提示使用者安裝該控制項時，提供由 Internet Explorer 顯示的資訊。  
  
```  
Signtool sign /f MyCert.pfx /d: "MyControl" /du http://www.example.com/MyControl/info.html MyControl.exe  
```  
  
 下列命令會為已數位簽署的檔案加上時間戳記。  
  
```  
signtool timestamp /t http://timestamp.verisign.com/scripts/timstamp.dll MyFile.exe  
```  
  
 下列命令會確認檔案是否已簽署。  
  
```  
signtool verify MyFile.exe  
```  
  
 下列命令會驗證可能已在目錄中簽署的系統檔。  
  
```  
signtool verify /a SystemFile.dll  
```  
  
 下列命令會驗證已在名為 `MyCatalog.cat` 之目錄中簽署的系統檔。  
  
```  
signtool verify /c MyCatalog.cat SystemFile.dll  
```  
  
## <a name="see-also"></a>另請參閱

- [工具](../../../docs/framework/tools/index.md)
- [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
