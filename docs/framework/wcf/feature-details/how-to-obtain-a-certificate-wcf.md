---
title: HOW TO：取得憑證 (WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 664eb62997123ea248b0b69700b86bf794646d4b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519218"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="f0895-102">HOW TO：取得憑證 (WCF)</span><span class="sxs-lookup"><span data-stu-id="f0895-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="f0895-103">若要使用任何 Windows Communication Foundation (WCF) 的功能，使用 X.509 憑證，您必須先取得憑證。</span><span class="sxs-lookup"><span data-stu-id="f0895-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="f0895-104">取得 X.509 憑證</span><span class="sxs-lookup"><span data-stu-id="f0895-104">To obtain an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="f0895-105">選擇下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="f0895-105">Choose one of the following:</span></span>  
  
    -   <span data-ttu-id="f0895-106">向憑證授權單位 (例如 VeriSign, Inc) 購買憑證。</span><span class="sxs-lookup"><span data-stu-id="f0895-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    -   <span data-ttu-id="f0895-107">設定自己的憑證服務，並且要求憑證授權單位簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="f0895-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="f0895-108">、Windows 2000 Server、Windows 2000 Server Datacenter 及 Windows 2000 Datacenter Server 都包含支援公開金鑰基礎結構 (PKI) 的憑證服務。</span><span class="sxs-lookup"><span data-stu-id="f0895-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="f0895-109">在 Windows Server 2008 中，使用[Active Directory 憑證服務](https://go.microsoft.com/fwlink/?LinkID=153483)角色來管理憑證授權單位。</span><span class="sxs-lookup"><span data-stu-id="f0895-109">In Windows Server 2008, use the [Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    -   <span data-ttu-id="f0895-110">設定自己的憑證服務，而不要簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="f0895-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f0895-111">不管您採用哪個方法，包含 X.509 憑證之 SOAP 要求的收件者都必須信任 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="f0895-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="f0895-112">這表示憑證鏈結中的 X.509 憑證或簽發者是在受信任人憑證存放區中，而 X.509 憑證不在不受信任的憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="f0895-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0895-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0895-113">See Also</span></span>  
 [<span data-ttu-id="f0895-114">使用憑證</span><span class="sxs-lookup"><span data-stu-id="f0895-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="f0895-115">如何：建立開發時要使用的暫時憑證</span><span class="sxs-lookup"><span data-stu-id="f0895-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
