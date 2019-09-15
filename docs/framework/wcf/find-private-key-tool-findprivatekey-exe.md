---
title: 尋找私密金鑰工具 (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 316f55b93cf4d867b99878bf483b73cb3f09ad04
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990345"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="8e320-102">尋找私密金鑰工具 (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="8e320-102">Find Private Key Tool (FindPrivateKey.exe)</span></span>

<span data-ttu-id="8e320-103">這個命令列工具可用於擷取憑證存放區的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="8e320-103">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="8e320-104">例如， *FindPrivateKey*可在憑證存放區中用來尋找與特定 x.509 憑證相關聯之私密金鑰檔案的位置和名稱。</span><span class="sxs-lookup"><span data-stu-id="8e320-104">For example, *FindPrivateKey.exe* can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8e320-105">FindPrivateKey 工具隨附做為 WCF 範例。</span><span class="sxs-lookup"><span data-stu-id="8e320-105">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="8e320-106">如需有關如何尋找範例和如何建立它的詳細資訊，請參閱[FindPrivateKey](./samples/findprivatekey.md)。</span><span class="sxs-lookup"><span data-stu-id="8e320-106">For more information about where to find the sample and how to build it, see [FindPrivateKey](./samples/findprivatekey.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="8e320-107">語法</span><span class="sxs-lookup"><span data-stu-id="8e320-107">Syntax</span></span>

```console
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a><span data-ttu-id="8e320-108">備註</span><span class="sxs-lookup"><span data-stu-id="8e320-108">Remarks</span></span>

<span data-ttu-id="8e320-109">下表說明可與尋找私密金鑰工具 (FindPrivateKey.exe) 搭配使用的引數和選項。</span><span class="sxs-lookup"><span data-stu-id="8e320-109">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>

|<span data-ttu-id="8e320-110">引數</span><span class="sxs-lookup"><span data-stu-id="8e320-110">Argument</span></span>|<span data-ttu-id="8e320-111">描述</span><span class="sxs-lookup"><span data-stu-id="8e320-111">Description</span></span>|
|--------------|-----------------|
|`storeName`|<span data-ttu-id="8e320-112">憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="8e320-112">Name of the certificate store.</span></span>|
|`storeLocation`|<span data-ttu-id="8e320-113">憑證存放區的位置。</span><span class="sxs-lookup"><span data-stu-id="8e320-113">The location of the certificate store.</span></span>|

|<span data-ttu-id="8e320-114">選項</span><span class="sxs-lookup"><span data-stu-id="8e320-114">Option</span></span>|<span data-ttu-id="8e320-115">說明</span><span class="sxs-lookup"><span data-stu-id="8e320-115">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="8e320-116">`/n <`*subjectName*`>`</span><span class="sxs-lookup"><span data-stu-id="8e320-116">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="8e320-117">指定憑證的主體名稱。</span><span class="sxs-lookup"><span data-stu-id="8e320-117">Specifies the subject name of the certificate.</span></span>|
|<span data-ttu-id="8e320-118">`/t <`*指紋*`>`</span><span class="sxs-lookup"><span data-stu-id="8e320-118">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="8e320-119">指定憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="8e320-119">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="8e320-120">您可以使用 Certmgr.exe 擷取憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="8e320-120">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|
|`/f`|<span data-ttu-id="8e320-121">僅輸出檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="8e320-121">Outputs the file name only.</span></span>|
|`/d`|<span data-ttu-id="8e320-122">僅輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="8e320-122">Outputs the directory only.</span></span>|
|`/a`|<span data-ttu-id="8e320-123">輸出絕對檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="8e320-123">Outputs the absolute file name.</span></span>|

## <a name="examples"></a><span data-ttu-id="8e320-124">範例</span><span class="sxs-lookup"><span data-stu-id="8e320-124">Examples</span></span>

<span data-ttu-id="8e320-125">下列命令會抓取 John Doe 的私密金鑰：</span><span class="sxs-lookup"><span data-stu-id="8e320-125">The following command retrieves the private key for John Doe:</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

<span data-ttu-id="8e320-126">下列命令會抓取本機電腦的私密金鑰：</span><span class="sxs-lookup"><span data-stu-id="8e320-126">The following command retrieves the private key for the local machine:</span></span>

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```
