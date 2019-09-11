---
title: Certmgr.exe (憑證管理員工具)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d13c2d2cc391e61c8ed764c26e5e5b5e7ea2a3bb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851379"
---
# <a name="certmgrexe-certificate-manager-tool"></a>Certmgr.exe (憑證管理員工具)
憑證管理員工具 (Certmgr.exe) 可以管理憑證、憑證信任清單 (CTL) 和憑證撤銷清單 (CRL)。  
  
 憑證管理員會隨 Visual Studio 自動安裝。 若要啟動工具，請使用[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
> [!NOTE]
> 憑證管理工具 (Certmgr.exe) 是一個命令列公用程式，而憑證 (Certmgr.msc) 則是 Microsoft Management Console (MMC) 嵌入式管理單元。 因為 Certmgr.msc 通常會位於 Windows 系統目錄中，以在命令列中輸入 `certmgr` 可能會載入憑證 MMC 嵌入式管理單元，即使您已開啟 Visual Studio 開發人員命令提示字元也一樣。 發生這種情況是因為嵌入式管理單元的路徑在 PATH 環境變數中位於憑證管理員工具的路徑之前。 如果您遇到此問題，可以透過指定可執行檔的路徑來執行 Certmgr.exe 指令。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 如需 X.509 憑證的概觀，請參閱[使用憑證](../../../docs/framework/wcf/feature-details/working-with-certificates.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a>參數  
  
|引數|描述|  
|--------------|-----------------|  
|*sourceStorename*|憑證存放區，包含現有的憑證、CTL，或是要新增、刪除、儲存或顯示的 CRL。 這可以是存放區檔或系統存放區。|  
|*destinationStorename*|輸出憑證存放區或檔案。|  
  
|選項|描述|  
|------------|-----------------|  
|**/add**|將憑證、CTL 和 CRL 加入憑證存放區。|  
|**/all**|與 **/add** 一起使用時會加入所有項目。 與 **/del** 一起使用時會刪除所有項目。未與 **/add** 或 **/del** 選項一起使用時，會顯示所有項目。 **/all** 選項無法與 **/put** 一起使用。|  
|**/c**|與 **/add** 一起使用時會加入憑證。 與 **/del** 一起使用時會刪除憑證。與 **/put** 一起使用時會儲存憑證。 未與 **/add**、 **/del** 或 **/put** 選項一起使用時，會顯示憑證。|  
|**/CRL**|與 **/add** 一起使用時會加入 CRL。 與 **/del** 一起使用時會刪除 CRL。與 **/put** 一起使用時會儲存 CRL。 未與 **/add**、 **/del** 或 **/put** 選項一起使用時，會顯示 CRL。|  
|**/CTL**|與 **/add** 一起使用時會加入 CTL。 與 **/del** 一起使用時會刪除 CTL。與 **/put** 一起使用時會儲存 CTL。 未與 **/add**、 **/del** 或 **/put** 選項一起使用時，會顯示 CTL。|  
|**/del**|從憑證存放區刪除憑證、CTL 和 CRL。|  
|**/e** *encodingType*|指定憑證的編碼類型。 預設為 `X509_ASN_ENCODING`。|  
|**/f** *dwFlags*|指定存放區的開放旗標。 這是傳遞到 **CertOpenStore** 的 *dwFlags* 參數。 預設值是 CERT_SYSTEM_STORE_CURRENT_USER。 只有在使用 **/y** 選項時，才會將這個選項列入考量。|  
|**/h**[**elp**]|顯示工具的命令語法和選項。|  
|**/n** *nam*|指定憑證的通用名稱來進行加入、刪除或儲存。 這個選項只能與憑證一起使用，無法與 CTL 或 CRL 一起使用。|  
|**/put**|將 X.509 憑證、CTL 或 CRL 從憑證存放區儲存到檔案。 檔案是以 X.509 格式儲存。 您可以將 **/7** 選項與 **/put** 選項一起使用，以 PKCS #7 格式儲存檔案。 **/put** 選項後面必須接著 **/c**、 **/CTL** 或 **/CRL** **/all** 選項無法與 **/put** 一起使用。|  
|**/r** *location*|識別系統存放區的登錄位置。 只有在指定 **/s** 選項時，才會將這個選項列入考量。 *location* 必須是下列其中一項：<br /><br /> -   `currentUser` 表示憑證存放區是在 HKEY_CURRENT_USER 機碼下方。 這是預設值。<br />-   `localMachine` 表示憑證存放區是在 HKEY_LOCAL_MACHINE 機碼下方。|  
|**/s**|指示憑證存放區是一個系統存放區。 如果不指定此選項，會將存放區視為 **StoreFile**。|  
|**/sha1** *sha1Hash*|指定憑證、CTL 或 CRL 的 SHA1 雜湊來進行加入、刪除或儲存。|  
|**/v**|指定詳細資訊模式；顯示憑證、CTL 和 CRL 的詳細資訊。 這個選項無法與 **/add**、 **/del** 或 **/put** 選項一起使用。|  
|**/y** *provider*|指定存放區提供者名稱。|  
|**/7**|將目的存放區儲存成 PKCS #7 物件。|  
|**/?**|顯示工具的命令語法和選項。|  
  
## <a name="remarks"></a>備註  
 Certmgr.exe 會執行下列幾種基本功能：  
  
- 將憑證、CTL 和 CRL 顯示到主控台。  
  
- 將憑證、CTL 和 CRL 加入憑證存放區。  
  
- 從憑證存放區刪除憑證、CTL 和 CRL。  
  
- 將 X.509 憑證、CTL 或 CRL 從憑證存放區儲存到檔案。  
  
 Certmgr.exe 可使用於兩種憑證存放區類型：**StoreFile** 和系統存放區。 您沒有必要指定憑證存放區的類型，Certmgr.exe 會識別存放區類型，並執行適當的作業。  
  
 在沒有指定任何選項的情況下執行 Certmgr.exe 將會啟動 certmgr.msc 嵌入式管理單元，這個單元含有 GUI，會幫助憑證管理工作，您也可以從命令列使用這些憑證管理工作。 GUI 提供一個可從磁碟將憑證、CTL 和 CRL 複製到憑證存放區的匯入精靈。  
  
 您可以編譯並執行下列程式碼以找到 X509Certificate 存放 `sourceStorename` 和 `destinationStorename` 參數的名字。  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 如需憑證的詳細資訊，請參閱[使用憑證](../../../docs/framework/wcf/feature-details/working-with-certificates.md)。  
  
## <a name="examples"></a>範例  
 下列命令會顯示叫做 `my` 且具有詳細資訊輸出的預設系統存放區。  
  
```console  
certmgr /v /s my  
```  
  
 下列命令會將 `myFile.ext` 檔案中的所有憑證加入到名為 `newFile.ext` 的新檔案中。  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 下列命令會將 `testcert.cer` 檔案中的憑證加入至 `my` 系統存放區。  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 下列命令會將 `TrustedCert.cer` 檔案中的憑證加入至根憑證存放區。  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 下列命令會將 `myCert` 系統存放區中通用名稱為 `my` 的憑證儲存到名為 `newCert.cer` 的檔案。  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 下列命令會刪除 `my` 系統存放區中的所有 CTL，並將產生的存放區儲存到名為 `newStore.str` 的檔案。  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 下列命令會將 `my` 系統存放區中的憑證儲存在 `newFile` 檔案。 系統會提示您輸入來自 `my` 的憑證號碼，以便放置在 `newFile` 中。  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a>另請參閱

- [工具](../../../docs/framework/tools/index.md)
- [Makecert.exe (憑證建立工具)](/windows/desktop/SecCrypto/makecert)
- [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
