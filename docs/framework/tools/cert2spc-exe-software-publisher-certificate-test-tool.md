---
title: Cert2spc.exe (軟體發行者憑證測試工具)
description: 使用 Cert2spc.exe 軟體發行者憑證測試控管。 此工具會從一或多個 x.509 憑證建立軟體發行者的憑證 (SPC) 。
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
ms.openlocfilehash: 0bcc785a51f2ca46195970130178d0cfa705ee6e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247319"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a>Cert2spc.exe (軟體發行者憑證測試工具)

軟體發行者憑證測試工具會從一個或多個 X.509 憑證建立軟體發行者的憑證 (SPC)。 Cert2spc.exe 僅供測試使用。 您可以從憑證授權單位 (例如 VeriSign 或 Thawte) 取得有效的 SPC。 如需建立 X.509 憑證的詳細資訊，請參閱 [Makecert.exe (憑證建立工具)](/windows/desktop/SecCrypto/makecert)。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](developer-command-prompt-for-vs.md)。  
  
 在命令提示字元中，請輸入下列項目：  
  
## <a name="syntax"></a>語法  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a>參數  
  
|引數|描述|  
|--------------|-----------------|  
|`certN.cer`|要包含在 SPC 檔案中的 X.509 憑證名稱。 您可以指定多個名稱，並以空格分隔每個名稱。|  
|`crlN.crl`|要包含在 SPC 檔案中的憑證撤銷清單名稱。 您可以指定多個名稱，並以空格分隔每個名稱。|  
|`outputSPCfile.spc`|將包含 X.509 憑證的 PKCS #7 物件名稱。|  
  
|選項|描述|  
|------------|-----------------|  
|**/?**|顯示工具的命令語法和選項。|  
  
## <a name="examples"></a>範例  

 下列命令會從 `myCertificate.cer` 建立 SPC 並且將它放入 `mySPCFile.spc` 中。  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 下列命令會從 `oneCertificate.cer` 和 `twoCertificate.cer` 建立 SPC 並且將它放入 `mySPCFile.spc` 中。  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a>另請參閱

- [工具](index.md)
- [Makecert.exe (憑證建立工具)](/windows/desktop/SecCrypto/makecert)
- [命令提示字元](developer-command-prompt-for-vs.md)
