---
title: 應用程式開發中的 PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b085604d7d20eb9222507b4820be219ffeae4726
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395732"
---
# <a name="pnrp-in-application-development"></a>應用程式開發中的 PNRP
在 Windows Vista 中，網路應用程式可以透過簡化的 PNRP 應用程式設計介面 (API)，存取名稱發行和解析功能。  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>實作對等名稱解析通訊協定  
 有了簡化的 PNRP API 之後，不會明確指定雲端來註冊名稱和位址；PNRP 元件會自動判斷要加入的適當雲端，以及雲端內要發行的位址。  
  
 針對 Windows Vista 中高度簡化的 PNRP 名稱解析，PNRP 名稱現在已整合至 getaddrinfo() Windows 通訊端函式。 若要使用 PNRP 將名稱解析為 IPv6 位址，應用程式可以使用 getaddrinfo() 函式解析完整網域名稱 (FQDN) name.prnp.net，其中 name 為要解析的對等名稱。 pnrp.net 網域是 Windows Vista 中專為 PNRP 名稱解析保留的網域。  
  
 在 PeerToPeer 應用程式之間傳遞的訊息仍然是透過基礎架構進行處理，例如 PeerChannel 和 WCF [大型資料與資料流](http://go.microsoft.com/fwlink/?LinkID=179652)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Net.PeerToPeer>
