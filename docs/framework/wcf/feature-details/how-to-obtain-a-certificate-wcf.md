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
# <a name="how-to-obtain-a-certificate-wcf"></a>HOW TO：取得憑證 (WCF)
若要使用 x.509 憑證的任何 Windows Communication Foundation (WCF) 功能，您只需要取得憑證。  
  
### <a name="to-obtain-an-x509-certificate"></a>取得 X.509 憑證  
  
1. 選擇下列其中之一：  
  
    - 向憑證授權單位 (例如 VeriSign, Inc) 購買憑證。  
  
    - 設定自己的憑證服務，並且要求憑證授權單位簽署憑證。 Windows Server 2003、Windows 2000 Server、Windows 2000 Server Datacenter 和 Windows 2000 Datacenter Server 都包含支援公開金鑰基礎結構 (PKI) 的憑證服務。 在 Windows Server 2008 中，請使用 [Active Directory 憑證服務](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) 角色來管理憑證授權單位單位。  
  
    - 設定自己的憑證服務，而不要簽署憑證。  
  
    > [!NOTE]
    > 不管您採用哪個方法，包含 X.509 憑證之 SOAP 要求的收件者都必須信任 X.509 憑證。 這表示憑證鏈結中的 X.509 憑證或簽發者是在受信任人憑證存放區中，而 X.509 憑證不在不受信任的憑證存放區中。  
  
## <a name="see-also"></a>另請參閱

- [使用憑證](working-with-certificates.md)
- [作法：建立開發時要使用的暫時憑證](how-to-create-temporary-certificates-for-use-during-development.md)
