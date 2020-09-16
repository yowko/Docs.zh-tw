---
title: HOW TO：取得憑證 (WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: b1fea1a7357b937bd15517b313948ead6aab894d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557849"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="72253-102">HOW TO：取得憑證 (WCF)</span><span class="sxs-lookup"><span data-stu-id="72253-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="72253-103">若要使用 x.509 憑證的任何 Windows Communication Foundation (WCF) 功能，您只需要取得憑證。</span><span class="sxs-lookup"><span data-stu-id="72253-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="72253-104">取得 X.509 憑證</span><span class="sxs-lookup"><span data-stu-id="72253-104">To obtain an X.509 certificate</span></span>  
  
1. <span data-ttu-id="72253-105">選擇下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="72253-105">Choose one of the following:</span></span>  
  
    - <span data-ttu-id="72253-106">向憑證授權單位 (例如 VeriSign, Inc) 購買憑證。</span><span class="sxs-lookup"><span data-stu-id="72253-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    - <span data-ttu-id="72253-107">設定自己的憑證服務，並且要求憑證授權單位簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="72253-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> <span data-ttu-id="72253-108">Windows Server 2003、Windows 2000 Server、Windows 2000 Server Datacenter 和 Windows 2000 Datacenter Server 都包含支援公開金鑰基礎結構 (PKI) 的憑證服務。</span><span class="sxs-lookup"><span data-stu-id="72253-108">Windows Server 2003, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="72253-109">在 Windows Server 2008 中，請使用 [Active Directory 憑證服務](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) 角色來管理憑證授權單位單位。</span><span class="sxs-lookup"><span data-stu-id="72253-109">In Windows Server 2008, use the [Active Directory Certificate Services](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) role to manage a certification authority.</span></span>  
  
    - <span data-ttu-id="72253-110">設定自己的憑證服務，而不要簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="72253-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="72253-111">不管您採用哪個方法，包含 X.509 憑證之 SOAP 要求的收件者都必須信任 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="72253-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="72253-112">這表示憑證鏈結中的 X.509 憑證或簽發者是在受信任人憑證存放區中，而 X.509 憑證不在不受信任的憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="72253-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72253-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72253-113">See also</span></span>

- [<span data-ttu-id="72253-114">使用憑證</span><span class="sxs-lookup"><span data-stu-id="72253-114">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="72253-115">作法：建立開發時要使用的暫時憑證</span><span class="sxs-lookup"><span data-stu-id="72253-115">How to: Create Temporary Certificates for Use During Development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
