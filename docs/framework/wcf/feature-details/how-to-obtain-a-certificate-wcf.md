---
title: 作法：取得憑證 (WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: e720a6742506f6270fda65de12f510c2a6224873
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929184"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>HOW TO：取得憑證 (WCF)
若要使用任何使用 x.509 憑證的 Windows Communication Foundation (WCF) 功能, 您只需要先取得憑證。  
  
### <a name="to-obtain-an-x509-certificate"></a>取得 X.509 憑證  
  
1. 選擇下列其中一項：  
  
    - 向憑證授權單位 (例如 VeriSign, Inc) 購買憑證。  
  
    - 設定自己的憑證服務，並且要求憑證授權單位簽署憑證。 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]、Windows 2000 Server、Windows 2000 Server Datacenter 及 Windows 2000 Datacenter Server 都包含支援公開金鑰基礎結構 (PKI) 的憑證服務。 在 Windows Server 2008 中, 使用 [ [Active Directory 憑證服務](https://go.microsoft.com/fwlink/?LinkID=153483)] 角色來管理憑證授權單位單位。  
  
    - 設定自己的憑證服務，而不要簽署憑證。  
  
    > [!NOTE]
    > 不管您採用哪個方法，包含 X.509 憑證之 SOAP 要求的收件者都必須信任 X.509 憑證。 這表示憑證鏈結中的 X.509 憑證或簽發者是在受信任人憑證存放區中，而 X.509 憑證不在不受信任的憑證存放區中。  
  
## <a name="see-also"></a>另請參閱

- [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [如何：建立要在開發期間使用的暫時憑證](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
