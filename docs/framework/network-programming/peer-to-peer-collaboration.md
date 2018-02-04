---
title: "對等共同作業"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 5060e12fb6a9fcc1bac1dfe6ccdcbaea9f2e6385
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="peer-to-peer-collaboration"></a>對等共同作業
對等網路使用功能相當強大的電腦 (個人電腦)，而這些電腦存在於網際網路邊緣，並且不只是用於進行用戶端運算工作。 現代的個人電腦 （電腦） 有非常快速的處理器、 大量的記憶體和大型硬碟，而這些做完全利用執行常見的運算工作，例如電子郵件及網頁瀏覽時。 現代電腦可以輕鬆地作為許多類型之應用程式的用戶端和伺服器 (對等)。  
  
-   對等共同作業基礎結構是簡化的 Microsoft Windows 對等基礎結構實作，其利用 Windows Vista 和更新版本的平台中的「近端分享」服務。 雖然它也可以服務網際網路端點或連絡人，但最適合用於「近端分享」服務在其上運作之子網路內具對等功能的應用程式。 它會合併 Live Messenger 和其他 Live 感知應用程式所使用的常見連絡人管理員，以判斷連絡端點、可用性和目前狀態。  
  
-  
  
## <a name="collaboration-applications"></a>共同作業應用程式  
 典型對等共同作業的應用包含下列步驟：  
  
-   對等可決定有興趣裝載共同作業工作階段之對等的身分識別  
  
-   以某種方式傳送主持工作階段的要求，而且主對等同意管理共同作業活動。  
  
-   主對等會邀請子網路上的連絡人 (包含要求者) 加入工作階段。  
  
-   所有想要共同作業的對等都可能會將主對等新增至其連絡人管理員。  
  
-   大部分的對等都會將邀請回應 (接受還是拒絕) 及時傳回給主對等。  
  
-   所有要共同作業的對等都會訂閱主對等。  
  
-   對等執行其初始共同作業活動的同時，主對等可能會將遠端對等新增至其連絡人管理員。 它也會處理所有邀請回應，判斷接受者、拒絕者和未回答者。  它可能會取消未回答者的邀請，或執行某個其他活動。  
  
-   目前，主對等可以啟動與所有受邀對等的共同作業工作階段，或註冊具有共同作業基礎結構的應用程式。  P2P 應用程式使用「對等共同作業基礎結構」和 <xref:System.Net.PeerToPeer.Collaboration> 命名空間來協調遊戲、電子佈告欄、會議和無伺服器目前狀態應用程式的通訊。  
  
-  
  
## <a name="peer-to-peer-networking-security"></a>對等網路安全性  
 在 Active Directory 網域中，網域控制站使用 Kerberos 提供驗證服務。 在無伺服器對等環境中，對等必須提供自己的驗證。 針對對等網路，任何節點都可以作為 CA，因此不需要每個對等之受信任根存放區中的根憑證。 使用格式為 X.509 憑證的自我簽署憑證來提供驗證。 這些憑證是由每個對等所建立，而每個對等都會產生公開金鑰/私密金鑰配對，以及使用私密金鑰所簽署的憑證。 自我簽署憑證用來進行驗證，以及提供對等實體的相關資訊。 與 X.509 驗證類似，對等網路驗證依賴追蹤回信任公開金鑰的憑證鏈。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Net.PeerToPeer.Collaboration>  
 [關於 System.Net.PeerToPeer.Collaboration 命名空間](../../../docs/framework/network-programming/about-the-system-net-peertopeer-collaboration-namespace.md)
