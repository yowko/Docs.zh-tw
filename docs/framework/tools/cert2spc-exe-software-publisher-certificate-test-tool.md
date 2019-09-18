---
title: Cert2spc.exe (軟體發行者憑證測試工具)
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a18c10df32b9e958147bd132a27a4dba47389cc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044799"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="2c795-102">Cert2spc.exe (軟體發行者憑證測試工具)</span><span class="sxs-lookup"><span data-stu-id="2c795-102">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="2c795-103">軟體發行者憑證測試工具會從一個或多個 X.509 憑證建立軟體發行者的憑證 (SPC)。</span><span class="sxs-lookup"><span data-stu-id="2c795-103">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="2c795-104">Cert2spc.exe 僅供測試使用。</span><span class="sxs-lookup"><span data-stu-id="2c795-104">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="2c795-105">您可以從憑證授權單位 (例如 VeriSign 或 Thawte) 取得有效的 SPC。</span><span class="sxs-lookup"><span data-stu-id="2c795-105">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="2c795-106">如需建立 X.509 憑證的詳細資訊，請參閱 [Makecert.exe (憑證建立工具)](/windows/desktop/SecCrypto/makecert)。</span><span class="sxs-lookup"><span data-stu-id="2c795-106">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert).</span></span>  
  
 <span data-ttu-id="2c795-107">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="2c795-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="2c795-108">若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="2c795-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="2c795-109">如需詳細資訊，請參閱[命令提示字元](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="2c795-109">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="2c795-110">在命令提示字元下輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="2c795-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c795-111">語法</span><span class="sxs-lookup"><span data-stu-id="2c795-111">Syntax</span></span>  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c795-112">參數</span><span class="sxs-lookup"><span data-stu-id="2c795-112">Parameters</span></span>  
  
|<span data-ttu-id="2c795-113">引數</span><span class="sxs-lookup"><span data-stu-id="2c795-113">Argument</span></span>|<span data-ttu-id="2c795-114">說明</span><span class="sxs-lookup"><span data-stu-id="2c795-114">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="2c795-115">要包含在 SPC 檔案中的 X.509 憑證名稱。</span><span class="sxs-lookup"><span data-stu-id="2c795-115">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="2c795-116">您可以指定多個名稱，並以空格分隔每個名稱。</span><span class="sxs-lookup"><span data-stu-id="2c795-116">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="2c795-117">要包含在 SPC 檔案中的憑證撤銷清單名稱。</span><span class="sxs-lookup"><span data-stu-id="2c795-117">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="2c795-118">您可以指定多個名稱，並以空格分隔每個名稱。</span><span class="sxs-lookup"><span data-stu-id="2c795-118">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="2c795-119">將包含 X.509 憑證的 PKCS #7 物件名稱。</span><span class="sxs-lookup"><span data-stu-id="2c795-119">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="2c795-120">選項</span><span class="sxs-lookup"><span data-stu-id="2c795-120">Option</span></span>|<span data-ttu-id="2c795-121">描述</span><span class="sxs-lookup"><span data-stu-id="2c795-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2c795-122">**/?**</span><span class="sxs-lookup"><span data-stu-id="2c795-122">**/?**</span></span>|<span data-ttu-id="2c795-123">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="2c795-123">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="2c795-124">範例</span><span class="sxs-lookup"><span data-stu-id="2c795-124">Examples</span></span>  
 <span data-ttu-id="2c795-125">下列命令會從 `myCertificate.cer` 建立 SPC 並且將它放入 `mySPCFile.spc` 中。</span><span class="sxs-lookup"><span data-stu-id="2c795-125">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="2c795-126">下列命令會從 `oneCertificate.cer` 和 `twoCertificate.cer` 建立 SPC 並且將它放入 `mySPCFile.spc` 中。</span><span class="sxs-lookup"><span data-stu-id="2c795-126">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c795-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c795-127">See also</span></span>

- [<span data-ttu-id="2c795-128">工具</span><span class="sxs-lookup"><span data-stu-id="2c795-128">Tools</span></span>](index.md)
- [<span data-ttu-id="2c795-129">Makecert.exe (憑證建立工具)</span><span class="sxs-lookup"><span data-stu-id="2c795-129">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="2c795-130">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="2c795-130">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
