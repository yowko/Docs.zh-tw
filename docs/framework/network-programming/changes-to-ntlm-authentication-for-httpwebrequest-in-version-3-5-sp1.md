---
title: "3.5 SP1 版中 HttpWebRequest 之 NTLM 驗證的變更"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 8bf0b428-5a21-4299-8d6e-bf8251fd978a
caps.latest.revision: 8
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 24abe4d2cc9a540f134ea32dbd6a44a630ff5524
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="changes-to-ntlm-authentication-for-httpwebrequest-in-version-35-sp1"></a>3.5 SP1 版中 HttpWebRequest 之 NTLM 驗證的變更
已在 .NET Framework 版本 3.5 SP1 和更新版本中進行安全性變更，這些變更會影響 <xref:System.Net.HttpWebRequest>、<xref:System.Net.HttpListener>、<xref:System.Net.Security.NegotiateStream> 以及 System.Net 命名空間中的相關類別處理整合式 Windows 驗證的方式。 這些變更可能會影響使用這些類別提出 Web 要求並接收回應的應用程式，而且其中使用根據 NTLM 的整合式 Windows 驗證。 這項變更可能會影響設定成使用整合式 Windows 驗證的網頁伺服器和用戶端應用程式。  
  
## <a name="overview"></a>概觀  
 整合式 Windows 驗證的設計可讓某些認證回應成為通用，這表示可以重複使用或轉寄它們。 如果不需要此特定設計功能，則驗證通訊協定應該執行目標特定資訊，以及通道特定資訊。 服務隨後可以提供延伸保護，確保認證回應包含服務特定資訊 (例如服務主體名稱 (SPN))。 在認證交換時利用此資訊，服務就能進一步免於惡意使用可能未正確取得的認證回應。  
  
 <xref:System.Net> 和 <xref:System.Net.Security> 命名空間中的多個元件都會代表呼叫端應用程式執行整合式 Windows 驗證。 本節描述在使用整合式 Windows 驗證時新增延伸保護的 System.Net 元件變更。  
  
## <a name="changes"></a>變更  
 與整合式 Windows 驗證搭配使用的 NTLM 驗證程序包含目的電腦所發出並傳回給用戶端電腦的挑戰。 除非連線是迴路連線 (例如，IPv4 位址 127.0.0.1)，否則電腦在收到它自己產生的挑戰時，驗證會失敗。  
  
 存取在內部網頁伺服器上執行的服務時，通常會使用與 http://contoso/service 或 https://contoso/service 類似的 URL 存取服務。 "contoso" 名稱通常不是服務部署所在電腦的電腦名稱。 使用 Active Directory、DNS、NetBIOS、本機電腦的 hosts 檔案 (例如，通常是 WINDOWS\system32\drivers\etc\hosts) 或本機電腦的 lmhosts 檔案 (例如，通常是 WINDOWS\system32\drivers\etc\lmhosts) 的 <xref:System.Net> 和相關命名空間支援，以將名稱解析為位址。 已解析名稱 "contoso"，以將傳送至 "contoso" 的要求傳送至適當的伺服器電腦。  
  
 針對大型部署進行設定時，也經常會將單一虛擬伺服器名稱授與用戶端應用程式和終端使用者絕不會使用之基礎電腦名稱的部署。 例如，您可能會呼叫 www.contoso.com 伺服器，但在內部網路上只需要使用 "contoso"。 此名稱稱為用戶端 Web 要求中的主機標頭。 根據 HTTP 通訊協定所指定，主機要求標頭欄位可指定所要求資源的網際網路主機和連接埠號碼。 這項資訊取自使用者或參考資源所提供的原始 URI (通常是 HTTP URL)。 在 .NET Framework 版本 4 上，用戶端也可以使用 <xref:System.Net.HttpWebRequest.Host%2A> 屬性來設定這項資訊。  
  
 <xref:System.Net.AuthenticationManager> 類別控制 <xref:System.Net.WebRequest> 衍生類別和 <xref:System.Net.WebClient> 類別所使用的 Managed 驗證元件 (「模組」)。 <xref:System.Net.AuthenticationManager> 類別提供屬性來公開以 URI 字串編製索引的 <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=fullName> 物件，讓應用程式提供要在驗證期間使用的自訂 SPN 字串。  
  
 如果未設定 <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> 屬性，版本 3.5 SP1 現在預設成指定 NTLM (NT LAN Manager) 驗證交換時 SPN 之要求 URL 中所使用的主機名稱。 要求 URL 中所使用的主機名稱可能不同於用戶端要求的 <xref:System.Net.HttpRequestHeader?displayProperty=fullName> 中所指定的主機標頭。 要求 URL 中所使用的主機名稱可能不同於伺服器的實際主機名稱、伺服器的電腦名稱、電腦的 IP 位址或迴路位址。 在這些情況下，Windows 會讓驗證要求失敗。 若要解決這個問題，我們需要通知 Windows：用戶端要求的要求 URL 中所使用的主機名稱 (例如，"contoso") 實際上是本機電腦的替代名稱。  
  
 有數種可行的方法可讓伺服器應用程式解決這項變更。 建議的方法是將要求 URL 中所使用的主機名稱對應至伺服器登錄中的 `BackConnectionHostNames` 機碼。 `BackConnectionHostNames` 登錄機碼通常用來將主機名稱對應至迴路位址。 步驟如下所列。  
  
 若要指定對應至迴路位址且可連線至本機電腦上網站的主機名稱，請遵循下列步驟：  
  
 1. 依序按一下 [開始] 和 [執行]，鍵入 regedit.exe，然後按一下 [確定]。  
  
 2. 在登錄編輯程式中，找到並按一下下列登錄機碼：  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0`  
  
 3. 以滑鼠右鍵按一下 MSV1_0，並指向 [新增]，然後按一下 [多字串值]。  
  
 4. 鍵入 `BackConnectionHostNames`，然後按 ENTER。  
  
 5. 以滑鼠右鍵按一下 `BackConnectionHostNames`，然後按一下 [修改]。  
  
 6. 在 [數值資料] 方塊中，鍵入主機名稱或本機電腦上網站的主機名稱 (要求 URL 中所使用的主機名稱)，然後按一下 [確定]。  
  
 7. 結束登錄編輯程式，然後重新啟動 IISAdmin 服務並執行 IISReset。  
  
 較不安全的因應措施是停用迴圈檢查，如 [http://support.microsoft.com/kb/896861](http://go.microsoft.com/fwlink/?LinkID=179657) 中所述。 這會停用反映攻擊的保護。 因此，最好只將這組替代名稱限制為預期電腦實際使用的替代名稱。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=fullName>   
 <xref:System.Net.HttpRequestHeader?displayProperty=fullName>   
 <xref:System.Net.HttpWebRequest.Host%2A?displayProperty=fullName>

