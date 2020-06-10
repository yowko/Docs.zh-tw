---
title: HOW TO：一律參考 X.509 憑證
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: c13dd5ebb18df62ce64fc74da53f3f5a2e8cadb7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599083"
---
# <a name="how-to-consistently-reference-x509-certificates"></a>HOW TO：一律參考 X.509 憑證
您可以用幾種方式來識別憑證：依據憑證的雜湊、依據簽發者和序號，或是依據主體金鑰識別元 (SKI)。 SKI 會提供憑證之主體公開金鑰的唯一識別，而且通常會在使用 XML 數位簽章時使用。 SKI 值通常是 x.509 憑證的一部分，作為*x.509 憑證延伸*。 Windows Communication Foundation （WCF）具有預設*參考樣式*，如果憑證中遺漏 SKI 延伸模組，則會使用簽發者和序號。 如果憑證包含 SKI 延伸，預設的參考樣式便會使用 SKI 來指向憑證。 如果在開發應用程式的過程中，您從使用未使用 SKI 延伸的憑證切換到使用 SKI 延伸模組的憑證，則 WCF 產生的訊息中所使用的參考樣式也會變更。  
  
 如果無論 SKI 延伸是否存在都必須使用一致的參考樣式，這時就可以設定需要的參考樣式，如下列程式碼所示。  
  
## <a name="example"></a>範例  
 下列範例會建立自訂的安全性繫結項目，該項目會使用單一的一致參考樣式、簽發者名稱及序號。  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 要編譯程式碼時，必須有下列命名空間：  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a>請參閱

- [Working with Certificates](working-with-certificates.md)
