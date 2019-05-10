---
title: HOW TO：取得憑證 (WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 1a2731c535bd403046ca3bc01364d0933f127a7f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643677"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="4acff-102">HOW TO：取得憑證 (WCF)</span><span class="sxs-lookup"><span data-stu-id="4acff-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="4acff-103">若要使用任何 Windows Communication Foundation (WCF) 的功能，使用 X.509 憑證，您必須先取得憑證。</span><span class="sxs-lookup"><span data-stu-id="4acff-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="4acff-104">取得 X.509 憑證</span><span class="sxs-lookup"><span data-stu-id="4acff-104">To obtain an X.509 certificate</span></span>  
  
1. <span data-ttu-id="4acff-105">選擇下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="4acff-105">Choose one of the following:</span></span>  
  
    - <span data-ttu-id="4acff-106">向憑證授權單位 (例如 VeriSign, Inc) 購買憑證。</span><span class="sxs-lookup"><span data-stu-id="4acff-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    - <span data-ttu-id="4acff-107">設定自己的憑證服務，並且要求憑證授權單位簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="4acff-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="4acff-108">、Windows 2000 Server、Windows 2000 Server Datacenter 及 Windows 2000 Datacenter Server 都包含支援公開金鑰基礎結構 (PKI) 的憑證服務。</span><span class="sxs-lookup"><span data-stu-id="4acff-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="4acff-109">在 Windows Server 2008 中，使用[Active Directory 憑證服務](https://go.microsoft.com/fwlink/?LinkID=153483)角色來管理憑證授權單位。</span><span class="sxs-lookup"><span data-stu-id="4acff-109">In Windows Server 2008, use the [Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    - <span data-ttu-id="4acff-110">設定自己的憑證服務，而不要簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="4acff-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4acff-111">不管您採用哪個方法，包含 X.509 憑證之 SOAP 要求的收件者都必須信任 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="4acff-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="4acff-112">這表示憑證鏈結中的 X.509 憑證或簽發者是在受信任人憑證存放區中，而 X.509 憑證不在不受信任的憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="4acff-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4acff-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4acff-113">See also</span></span>

- [<span data-ttu-id="4acff-114">使用憑證</span><span class="sxs-lookup"><span data-stu-id="4acff-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="4acff-115">如何：在開發期間，用於建立暫時憑證</span><span class="sxs-lookup"><span data-stu-id="4acff-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
