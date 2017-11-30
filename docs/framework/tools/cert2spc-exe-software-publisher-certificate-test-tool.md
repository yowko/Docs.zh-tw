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
ms.openlocfilehash: c720da81c63b612201ede5f648f6861470b25bee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="eb1d9-102">Cert2spc.exe (軟體發行者憑證測試工具)</span><span class="sxs-lookup"><span data-stu-id="eb1d9-102">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="eb1d9-103">軟體發行者憑證測試工具會從一個或多個 X.509 憑證建立軟體發行者的憑證 (SPC)。</span><span class="sxs-lookup"><span data-stu-id="eb1d9-103">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="eb1d9-104">Cert2spc.exe 僅供測試使用。</span><span class="sxs-lookup"><span data-stu-id="eb1d9-104">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="eb1d9-105">您可以從憑證授權單位 (例如 VeriSign 或 Thawte) 取得有效的 SPC。</span><span class="sxs-lookup"><span data-stu-id="eb1d9-105">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="eb1d9-106">如需建立 X.509 憑證的詳細資訊，請參閱 [Makecert.exe (憑證建立工具)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)。</span><span class="sxs-lookup"><span data-stu-id="eb1d9-106">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).</span></span>  
  
 <span data-ttu-id="eb1d9-107">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="eb1d9-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="eb1d9-108">若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="eb1d9-108">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="eb1d9-109">如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="eb1d9-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="eb1d9-110">在命令提示字元下輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="eb1d9-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb1d9-111">語法</span><span class="sxs-lookup"><span data-stu-id="eb1d9-111">Syntax</span></span>  
  
```  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb1d9-112">參數</span><span class="sxs-lookup"><span data-stu-id="eb1d9-112">Parameters</span></span>  
  
|<span data-ttu-id="eb1d9-113">引數</span><span class="sxs-lookup"><span data-stu-id="eb1d9-113">Argument</span></span>|<span data-ttu-id="eb1d9-114">說明</span><span class="sxs-lookup"><span data-stu-id="eb1d9-114">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="eb1d9-115">要包含在 SPC 檔案中的 X.509 憑證名稱。</span><span class="sxs-lookup"><span data-stu-id="eb1d9-115">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="eb1d9-116">您可以指定多個名稱，並以空格分隔每個名稱。</span><span class="sxs-lookup"><span data-stu-id="eb1d9-116">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="eb1d9-117">要包含在 SPC 檔案中的憑證撤銷清單名稱。</span><span class="sxs-lookup"><span data-stu-id="eb1d9-117">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="eb1d9-118">您可以指定多個名稱，並以空格分隔每個名稱。</span><span class="sxs-lookup"><span data-stu-id="eb1d9-118">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="eb1d9-119">將包含 X.509 憑證的 PKCS #7 物件名稱。</span><span class="sxs-lookup"><span data-stu-id="eb1d9-119">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="eb1d9-120">選項</span><span class="sxs-lookup"><span data-stu-id="eb1d9-120">Option</span></span>|<span data-ttu-id="eb1d9-121">描述</span><span class="sxs-lookup"><span data-stu-id="eb1d9-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="eb1d9-122">**/?**</span><span class="sxs-lookup"><span data-stu-id="eb1d9-122">**/?**</span></span>|<span data-ttu-id="eb1d9-123">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="eb1d9-123">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="eb1d9-124">範例</span><span class="sxs-lookup"><span data-stu-id="eb1d9-124">Examples</span></span>  
 <span data-ttu-id="eb1d9-125">下列命令會從 `myCertificate.cer` 建立 SPC 並且將它放入 `mySPCFile.spc` 中。</span><span class="sxs-lookup"><span data-stu-id="eb1d9-125">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```  
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="eb1d9-126">下列命令會從 `oneCertificate.cer` 和 `twoCertificate.cer` 建立 SPC 並且將它放入 `mySPCFile.spc` 中。</span><span class="sxs-lookup"><span data-stu-id="eb1d9-126">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```  
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb1d9-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb1d9-127">See Also</span></span>  
 [<span data-ttu-id="eb1d9-128">工具</span><span class="sxs-lookup"><span data-stu-id="eb1d9-128">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="eb1d9-129">Makecert.exe （憑證建立工具）</span><span class="sxs-lookup"><span data-stu-id="eb1d9-129">Makecert.exe (Certificate Creation Tool)</span></span>](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [<span data-ttu-id="eb1d9-130">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="eb1d9-130">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
