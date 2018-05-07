---
title: 尋找私密金鑰工具 (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 8f156cbb2f4fad8d51e356bd4dee2d72d9397ffb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>尋找私密金鑰工具 (FindPrivateKey.exe)

這個命令列工具可用於擷取憑證存放區的私密金鑰。 例如， *FindPrivateKey.exe*可用來尋找與特定 X.509 憑證的憑證存放區相關聯的私密金鑰檔案的名稱與位置。

> [!IMPORTANT]
> FindPrivateKey 工具隨附做為 WCF 範例。 如需如何尋找範例以及如何建立它的詳細資訊，請參閱[FindPrivateKey](./samples/findprivatekey.md)。

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

|選項|描述|
|------------|-----------------|
|`/n <` *subjectName* `>`|指定憑證的主體名稱。|
|`/t <` *憑證指紋* `>`|指定憑證的指紋。 您可以使用 Certmgr.exe 擷取憑證的指紋。|
|`/f`|僅輸出檔案名稱。|
|`/d`|僅輸出目錄。|
|`/a`|輸出絕對檔案名稱。|

## <a name="examples"></a>範例

下列命令會擷取 John doe 的私密金鑰：

```
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

下列命令會擷取本機電腦的私密金鑰：

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```