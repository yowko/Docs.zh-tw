---
title: HOW TO：取得憑證 (WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: d020f3e97023d07abb572d30dd53896bfec1da46
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597016"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="9ccc0-102">HOW TO：取得憑證 (WCF)</span><span class="sxs-lookup"><span data-stu-id="9ccc0-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="9ccc0-103">若要使用任何使用 x.509 憑證的 Windows Communication Foundation （WCF）功能，您只需要先取得憑證。</span><span class="sxs-lookup"><span data-stu-id="9ccc0-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="9ccc0-104">取得 X.509 憑證</span><span class="sxs-lookup"><span data-stu-id="9ccc0-104">To obtain an X.509 certificate</span></span>  
  
1. <span data-ttu-id="9ccc0-105">選擇下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="9ccc0-105">Choose one of the following:</span></span>  
  
    - <span data-ttu-id="9ccc0-106">向憑證授權單位 (例如 VeriSign, Inc) 購買憑證。</span><span class="sxs-lookup"><span data-stu-id="9ccc0-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    - <span data-ttu-id="9ccc0-107">設定自己的憑證服務，並且要求憑證授權單位簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="9ccc0-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> <span data-ttu-id="9ccc0-108">Windows Server 2003、Windows 2000 Server、Windows 2000 Server Datacenter 和 Windows 2000 Datacenter Server 全都包含支援公開金鑰基礎結構（PKI）的憑證服務。</span><span class="sxs-lookup"><span data-stu-id="9ccc0-108">Windows Server 2003, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="9ccc0-109">在 Windows Server 2008 中，使用 [ [Active Directory 憑證服務](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10))] 角色來管理憑證授權單位單位。</span><span class="sxs-lookup"><span data-stu-id="9ccc0-109">In Windows Server 2008, use the [Active Directory Certificate Services](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) role to manage a certification authority.</span></span>  
  
    - <span data-ttu-id="9ccc0-110">設定自己的憑證服務，而不要簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="9ccc0-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9ccc0-111">不管您採用哪個方法，包含 X.509 憑證之 SOAP 要求的收件者都必須信任 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="9ccc0-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="9ccc0-112">這表示憑證鏈結中的 X.509 憑證或簽發者是在受信任人憑證存放區中，而 X.509 憑證不在不受信任的憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="9ccc0-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ccc0-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="9ccc0-113">See also</span></span>

- [<span data-ttu-id="9ccc0-114">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="9ccc0-114">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="9ccc0-115">HOW TO：建立開發時要使用的暫時憑證</span><span class="sxs-lookup"><span data-stu-id="9ccc0-115">How to: Create Temporary Certificates for Use During Development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
