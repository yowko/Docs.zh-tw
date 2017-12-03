---
title: "HOW TO：取得憑證 (WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1b7ab4ed91487965ac8b0d78a9a44818cfee9eb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-obtain-a-certificate-wcf"></a>HOW TO：取得憑證 (WCF)
為了使用任何一種使用 X.509 憑證的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 功能，您必須先取得憑證。  
  
### <a name="to-obtain-an-x509-certificate"></a>取得 X.509 憑證  
  
1.  選擇下列其中一項：  
  
    -   向憑證授權單位 (例如 VeriSign, Inc) 購買憑證。  
  
    -   設定自己的憑證服務，並且要求憑證授權單位簽署憑證。 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]、Windows 2000 Server、Windows 2000 Server Datacenter 及 Windows 2000 Datacenter Server 都包含支援公開金鑰基礎結構 (PKI) 的憑證服務。 在 Windows Server 2008 中，使用[Active Directory 憑證服務](http://go.microsoft.com/fwlink/?LinkID=153483)角色來管理憑證授權單位。  
  
    -   設定自己的憑證服務，而不要簽署憑證。  
  
    > [!NOTE]
    >  不管您採用哪個方法，包含 X.509 憑證之 SOAP 要求的收件者都必須信任 X.509 憑證。 這表示憑證鏈結中的 X.509 憑證或簽發者是在受信任人憑證存放區中，而 X.509 憑證不在不受信任的憑證存放區中。  
  
## <a name="see-also"></a>另請參閱  
 [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [如何： 建立開發時使用的暫時憑證](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
