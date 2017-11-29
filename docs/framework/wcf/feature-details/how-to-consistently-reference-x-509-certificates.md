---
title: "HOW TO：一律參考 X.509 憑證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d42af919b9792fc5a5303737187be7ffef6405d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-consistently-reference-x509-certificates"></a><span data-ttu-id="1d3e6-102">HOW TO：一律參考 X.509 憑證</span><span class="sxs-lookup"><span data-stu-id="1d3e6-102">How to: Consistently Reference X.509 Certificates</span></span>
<span data-ttu-id="1d3e6-103">您可以用幾種方式來識別憑證：依據憑證的雜湊、依據簽發者和序號，或是依據主體金鑰識別元 (SKI)。</span><span class="sxs-lookup"><span data-stu-id="1d3e6-103">You can identify a certificate in several ways: by the hash of the certificate, by the issuer and serial number, or by the subject key identifier (SKI).</span></span> <span data-ttu-id="1d3e6-104">SKI 會提供憑證之主體公開金鑰的唯一識別，而且通常會在使用 XML 數位簽章時使用。</span><span class="sxs-lookup"><span data-stu-id="1d3e6-104">The SKI provides a unique identification for the certificate's subject public key and is often used when working with XML digital signing.</span></span> <span data-ttu-id="1d3e6-105">SKI 值通常是做為 X.509 憑證的部分*X.509 憑證延伸*。</span><span class="sxs-lookup"><span data-stu-id="1d3e6-105">The SKI value is usually part of the X.509 certificate as an *X.509 certificate extension*.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="1d3e6-106">有了 default*參考樣式*憑證中遺失 SKI 延伸是否使用簽發者和序號。</span><span class="sxs-lookup"><span data-stu-id="1d3e6-106"> has a default *referencing style* that uses the issuer and serial number if the SKI extension is missing from the certificate.</span></span> <span data-ttu-id="1d3e6-107">如果憑證包含 SKI 延伸，預設的參考樣式便會使用 SKI 來指向憑證。</span><span class="sxs-lookup"><span data-stu-id="1d3e6-107">If the certificate contains the SKI extension, the default referencing style uses the SKI to point to the certificate.</span></span> <span data-ttu-id="1d3e6-108">如果在開發應用程式的期間，您從使用不用 SKI 延伸的憑證切換到使用 SKI 延伸的憑證，在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 產生之訊息中所使用的參考樣式也會變更。</span><span class="sxs-lookup"><span data-stu-id="1d3e6-108">If mid-way through development of an application, you switch from using certificates that do not use the SKI extension to certificates that use the SKI extension, the referencing style used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-generated messages also changes.</span></span>  
  
 <span data-ttu-id="1d3e6-109">如果無論 SKI 延伸是否存在都必須使用一致的參考樣式，這時就可以設定需要的參考樣式，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="1d3e6-109">If a consistent referencing style is required regardless of SKI extension presence, it is possible to configure the desired referencing style as shown in the following code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d3e6-110">範例</span><span class="sxs-lookup"><span data-stu-id="1d3e6-110">Example</span></span>  
 <span data-ttu-id="1d3e6-111">下列範例會建立自訂的安全性繫結項目，該項目會使用單一的一致參考樣式、簽發者名稱及序號。</span><span class="sxs-lookup"><span data-stu-id="1d3e6-111">The following example creates a custom security binding element that uses a single consistent referencing style, the issuer name and serial number.</span></span>  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1d3e6-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1d3e6-112">Compiling the Code</span></span>  
 <span data-ttu-id="1d3e6-113">要編譯程式碼時，必須有下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="1d3e6-113">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a><span data-ttu-id="1d3e6-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d3e6-114">See Also</span></span>  
 [<span data-ttu-id="1d3e6-115">使用憑證</span><span class="sxs-lookup"><span data-stu-id="1d3e6-115">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
