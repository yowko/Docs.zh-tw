---
title: "Cert2spc.exe (軟體發行者憑證測試工具)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5a8363b0ec059c1ae94b7ab53e5c3064a06541f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a>Cert2spc.exe (軟體發行者憑證測試工具)
軟體發行者憑證測試工具會從一個或多個 X.509 憑證建立軟體發行者的憑證 (SPC)。 Cert2spc.exe 僅供測試使用。 您可以從憑證授權單位 (例如 VeriSign 或 Thawte) 取得有效的 SPC。 如需建立 X.509 憑證的詳細資訊，請參閱 [Makecert.exe (憑證建立工具)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
#### <a name="parameters"></a>參數  
  
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
  
```  
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 下列命令會從 `oneCertificate.cer` 和 `twoCertificate.cer` 建立 SPC 並且將它放入 `mySPCFile.spc` 中。  
  
```  
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a>請參閱  
 [工具](../../../docs/framework/tools/index.md)  
 [Makecert.exe (憑證建立工具)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
