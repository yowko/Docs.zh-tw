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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5e2110e129b293ffb04c8e3eb69a5c3bfe83c17b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="a2c5a-102">尋找私密金鑰工具 (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="a2c5a-102">Find Private Key Tool (FindPrivateKey.exe)</span></span>
<span data-ttu-id="a2c5a-103">這個命令列工具可用於擷取憑證存放區的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="a2c5a-103">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="a2c5a-104">例如，FindPrivateKey.exe 可用來在憑證存放區中尋找與特定 X.509 憑證關聯的私密金鑰其位置和名稱。</span><span class="sxs-lookup"><span data-stu-id="a2c5a-104">For example, FindPrivateKey.exe can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a2c5a-105">FindPrivateKey 工具隨附做為 WCF 範例。</span><span class="sxs-lookup"><span data-stu-id="a2c5a-105">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="a2c5a-106">如需何處尋找範例及如何進行建置的詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="a2c5a-106">For more information about where to find the sample and how to build it, see</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2c5a-107">語法</span><span class="sxs-lookup"><span data-stu-id="a2c5a-107">Syntax</span></span>  
  
```  
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
## <a name="remarks"></a><span data-ttu-id="a2c5a-108">備註</span><span class="sxs-lookup"><span data-stu-id="a2c5a-108">Remarks</span></span>  
 <span data-ttu-id="a2c5a-109">下表說明可與尋找私密金鑰工具 (FindPrivateKey.exe) 搭配使用的引數和選項。</span><span class="sxs-lookup"><span data-stu-id="a2c5a-109">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>  
  
|<span data-ttu-id="a2c5a-110">引數</span><span class="sxs-lookup"><span data-stu-id="a2c5a-110">Argument</span></span>|<span data-ttu-id="a2c5a-111">描述</span><span class="sxs-lookup"><span data-stu-id="a2c5a-111">Description</span></span>|  
|--------------|-----------------|  
|`storeName`|<span data-ttu-id="a2c5a-112">憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="a2c5a-112">Name of the certificate store.</span></span>|  
|`storeLocation`|<span data-ttu-id="a2c5a-113">憑證存放區的位置。</span><span class="sxs-lookup"><span data-stu-id="a2c5a-113">The location of the certificate store.</span></span>|  
  
|<span data-ttu-id="a2c5a-114">選項</span><span class="sxs-lookup"><span data-stu-id="a2c5a-114">Option</span></span>|<span data-ttu-id="a2c5a-115">說明</span><span class="sxs-lookup"><span data-stu-id="a2c5a-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a2c5a-116">`/n <`*subjectName*`>`</span><span class="sxs-lookup"><span data-stu-id="a2c5a-116">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="a2c5a-117">指定憑證的主體名稱。</span><span class="sxs-lookup"><span data-stu-id="a2c5a-117">Specifies the subject name of the certificate.</span></span>|  
|<span data-ttu-id="a2c5a-118">`/t <`*指紋*`>`</span><span class="sxs-lookup"><span data-stu-id="a2c5a-118">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="a2c5a-119">指定憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="a2c5a-119">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="a2c5a-120">您可以使用 Certmgr.exe 擷取憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="a2c5a-120">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|  
|`/f`|<span data-ttu-id="a2c5a-121">僅輸出檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="a2c5a-121">Outputs the file name only.</span></span>|  
|`/d`|<span data-ttu-id="a2c5a-122">僅輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="a2c5a-122">Outputs the directory only.</span></span>|  
|`/a`|<span data-ttu-id="a2c5a-123">輸出絕對檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="a2c5a-123">Outputs the absolute file name.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="a2c5a-124">範例</span><span class="sxs-lookup"><span data-stu-id="a2c5a-124">Examples</span></span>  
 <span data-ttu-id="a2c5a-125">下列命令會擷取 John Doe 的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="a2c5a-125">The following command retrieves the private key for John Doe.</span></span>  
  
```  
FindPrivateKey My CurrentUser -n "CN=John Doe"  
```  
  
 <span data-ttu-id="a2c5a-126">下列命令會擷取本機電腦的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="a2c5a-126">The following command retrieves the private key for the local machine.</span></span>  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a  
```
