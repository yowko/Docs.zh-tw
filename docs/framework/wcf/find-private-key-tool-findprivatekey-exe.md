---
title: "尋找私密金鑰工具 (FindPrivateKey.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f542e0ba3bf35319c270fe9f93d3f355cc45ac95
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>尋找私密金鑰工具 (FindPrivateKey.exe)
這個命令列工具可用於擷取憑證存放區的私密金鑰。 例如，FindPrivateKey.exe 可用來在憑證存放區中尋找與特定 X.509 憑證關聯的私密金鑰其位置和名稱。  
  
> [!IMPORTANT]
>  FindPrivateKey 工具隨附做為 WCF 範例。 如需何處尋找範例及如何進行建置的詳細資訊，請參閱  
  
## <a name="syntax"></a>語法  
  
```  
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
## <a name="remarks"></a>備註  
 下表說明可與尋找私密金鑰工具 (FindPrivateKey.exe) 搭配使用的引數和選項。  
  
|引數|描述|  
|--------------|-----------------|  
|`storeName`|憑證存放區的名稱。|  
|`storeLocation`|憑證存放區的位置。|  
  
|選項|說明|  
|------------|-----------------|  
|`/n <`*subjectName*`>`|指定憑證的主體名稱。|  
|`/t <`*指紋*`>`|指定憑證的指紋。 您可以使用 Certmgr.exe 擷取憑證的指紋。|  
|`/f`|僅輸出檔案名稱。|  
|`/d`|僅輸出目錄。|  
|`/a`|輸出絕對檔案名稱。|  
  
## <a name="examples"></a>範例  
 下列命令會擷取 John Doe 的私密金鑰。  
  
```  
FindPrivateKey My CurrentUser -n "CN=John Doe"  
```  
  
 下列命令會擷取本機電腦的私密金鑰。  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a  
```
