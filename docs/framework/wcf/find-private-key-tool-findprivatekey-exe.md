---
title: 尋找私密金鑰工具 (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 8f156cbb2f4fad8d51e356bd4dee2d72d9397ffb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929580"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="24fd0-102">尋找私密金鑰工具 (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="24fd0-102">Find Private Key Tool (FindPrivateKey.exe)</span></span>

<span data-ttu-id="24fd0-103">這個命令列工具可用於擷取憑證存放區的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="24fd0-103">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="24fd0-104">例如， *FindPrivateKey.exe*可用來尋找與特定 X.509 憑證的憑證存放區相關聯的私用金鑰檔的名稱與位置。</span><span class="sxs-lookup"><span data-stu-id="24fd0-104">For example, *FindPrivateKey.exe* can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24fd0-105">FindPrivateKey 工具隨附做為 WCF 範例。</span><span class="sxs-lookup"><span data-stu-id="24fd0-105">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="24fd0-106">如需有關尋找範例的位置，以及如何建置它的詳細資訊，請參閱[FindPrivateKey](./samples/findprivatekey.md)。</span><span class="sxs-lookup"><span data-stu-id="24fd0-106">For more information about where to find the sample and how to build it, see [FindPrivateKey](./samples/findprivatekey.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="24fd0-107">語法</span><span class="sxs-lookup"><span data-stu-id="24fd0-107">Syntax</span></span>

```
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a><span data-ttu-id="24fd0-108">備註</span><span class="sxs-lookup"><span data-stu-id="24fd0-108">Remarks</span></span>

<span data-ttu-id="24fd0-109">下表說明可與尋找私密金鑰工具 (FindPrivateKey.exe) 搭配使用的引數和選項。</span><span class="sxs-lookup"><span data-stu-id="24fd0-109">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>

|<span data-ttu-id="24fd0-110">引數</span><span class="sxs-lookup"><span data-stu-id="24fd0-110">Argument</span></span>|<span data-ttu-id="24fd0-111">描述</span><span class="sxs-lookup"><span data-stu-id="24fd0-111">Description</span></span>|
|--------------|-----------------|
|`storeName`|<span data-ttu-id="24fd0-112">憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="24fd0-112">Name of the certificate store.</span></span>|
|`storeLocation`|<span data-ttu-id="24fd0-113">憑證存放區的位置。</span><span class="sxs-lookup"><span data-stu-id="24fd0-113">The location of the certificate store.</span></span>|

|<span data-ttu-id="24fd0-114">選項</span><span class="sxs-lookup"><span data-stu-id="24fd0-114">Option</span></span>|<span data-ttu-id="24fd0-115">描述</span><span class="sxs-lookup"><span data-stu-id="24fd0-115">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="24fd0-116">`/n <` *subjectName* `>`</span><span class="sxs-lookup"><span data-stu-id="24fd0-116">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="24fd0-117">指定憑證的主體名稱。</span><span class="sxs-lookup"><span data-stu-id="24fd0-117">Specifies the subject name of the certificate.</span></span>|
|<span data-ttu-id="24fd0-118">`/t <` *憑證指紋* `>`</span><span class="sxs-lookup"><span data-stu-id="24fd0-118">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="24fd0-119">指定憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="24fd0-119">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="24fd0-120">您可以使用 Certmgr.exe 擷取憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="24fd0-120">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|
|`/f`|<span data-ttu-id="24fd0-121">僅輸出檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="24fd0-121">Outputs the file name only.</span></span>|
|`/d`|<span data-ttu-id="24fd0-122">僅輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="24fd0-122">Outputs the directory only.</span></span>|
|`/a`|<span data-ttu-id="24fd0-123">輸出絕對檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="24fd0-123">Outputs the absolute file name.</span></span>|

## <a name="examples"></a><span data-ttu-id="24fd0-124">範例</span><span class="sxs-lookup"><span data-stu-id="24fd0-124">Examples</span></span>

<span data-ttu-id="24fd0-125">下列命令會擷取 John doe 的私密金鑰：</span><span class="sxs-lookup"><span data-stu-id="24fd0-125">The following command retrieves the private key for John Doe:</span></span>

```
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

<span data-ttu-id="24fd0-126">下列命令會擷取本機電腦的私密金鑰：</span><span class="sxs-lookup"><span data-stu-id="24fd0-126">The following command retrieves the private key for the local machine:</span></span>

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```