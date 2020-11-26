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
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="8bb44-104">Cert2spc.exe (軟體發行者憑證測試工具)</span><span class="sxs-lookup"><span data-stu-id="8bb44-104">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>

<span data-ttu-id="8bb44-105">軟體發行者憑證測試工具會從一個或多個 X.509 憑證建立軟體發行者的憑證 (SPC)。</span><span class="sxs-lookup"><span data-stu-id="8bb44-105">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="8bb44-106">Cert2spc.exe 僅供測試使用。</span><span class="sxs-lookup"><span data-stu-id="8bb44-106">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="8bb44-107">您可以從憑證授權單位 (例如 VeriSign 或 Thawte) 取得有效的 SPC。</span><span class="sxs-lookup"><span data-stu-id="8bb44-107">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="8bb44-108">如需建立 X.509 憑證的詳細資訊，請參閱 [Makecert.exe (憑證建立工具)](/windows/desktop/SecCrypto/makecert)。</span><span class="sxs-lookup"><span data-stu-id="8bb44-108">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert).</span></span>  
  
 <span data-ttu-id="8bb44-109">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="8bb44-109">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="8bb44-110">若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="8bb44-110">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="8bb44-111">如需詳細資訊，請參閱[命令提示字元](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="8bb44-111">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="8bb44-112">在命令提示字元中，請輸入下列項目：</span><span class="sxs-lookup"><span data-stu-id="8bb44-112">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bb44-113">語法</span><span class="sxs-lookup"><span data-stu-id="8bb44-113">Syntax</span></span>  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bb44-114">參數</span><span class="sxs-lookup"><span data-stu-id="8bb44-114">Parameters</span></span>  
  
|<span data-ttu-id="8bb44-115">引數</span><span class="sxs-lookup"><span data-stu-id="8bb44-115">Argument</span></span>|<span data-ttu-id="8bb44-116">描述</span><span class="sxs-lookup"><span data-stu-id="8bb44-116">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="8bb44-117">要包含在 SPC 檔案中的 X.509 憑證名稱。</span><span class="sxs-lookup"><span data-stu-id="8bb44-117">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="8bb44-118">您可以指定多個名稱，並以空格分隔每個名稱。</span><span class="sxs-lookup"><span data-stu-id="8bb44-118">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="8bb44-119">要包含在 SPC 檔案中的憑證撤銷清單名稱。</span><span class="sxs-lookup"><span data-stu-id="8bb44-119">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="8bb44-120">您可以指定多個名稱，並以空格分隔每個名稱。</span><span class="sxs-lookup"><span data-stu-id="8bb44-120">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="8bb44-121">將包含 X.509 憑證的 PKCS #7 物件名稱。</span><span class="sxs-lookup"><span data-stu-id="8bb44-121">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="8bb44-122">選項</span><span class="sxs-lookup"><span data-stu-id="8bb44-122">Option</span></span>|<span data-ttu-id="8bb44-123">描述</span><span class="sxs-lookup"><span data-stu-id="8bb44-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8bb44-124">**/?**</span><span class="sxs-lookup"><span data-stu-id="8bb44-124">**/?**</span></span>|<span data-ttu-id="8bb44-125">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="8bb44-125">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="8bb44-126">範例</span><span class="sxs-lookup"><span data-stu-id="8bb44-126">Examples</span></span>  

 <span data-ttu-id="8bb44-127">下列命令會從 `myCertificate.cer` 建立 SPC 並且將它放入 `mySPCFile.spc` 中。</span><span class="sxs-lookup"><span data-stu-id="8bb44-127">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="8bb44-128">下列命令會從 `oneCertificate.cer` 和 `twoCertificate.cer` 建立 SPC 並且將它放入 `mySPCFile.spc` 中。</span><span class="sxs-lookup"><span data-stu-id="8bb44-128">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="8bb44-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bb44-129">See also</span></span>

- [<span data-ttu-id="8bb44-130">工具</span><span class="sxs-lookup"><span data-stu-id="8bb44-130">Tools</span></span>](index.md)
- [<span data-ttu-id="8bb44-131">Makecert.exe (憑證建立工具)</span><span class="sxs-lookup"><span data-stu-id="8bb44-131">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="8bb44-132">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="8bb44-132">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
