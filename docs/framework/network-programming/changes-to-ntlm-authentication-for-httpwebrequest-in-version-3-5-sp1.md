---
title: "3.5 SP1 版中 HttpWebRequest 之 NTLM 驗證的變更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 8bf0b428-5a21-4299-8d6e-bf8251fd978a
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# 3.5 SP1 版中 HttpWebRequest 之 NTLM 驗證的變更
安全性已發生變更 .NET Framework 3.5 版 SP1 \(含\) 以後版本會影響整合式 Windows 驗證的方式。 <xref:System.Net.HttpWebRequest>、 <xref:System.Net.HttpListener>、 <xref:System.Net.Security.NegotiateStream>和相關類別處理 System.Net 命名空間。  這些變更可能會影響使用這些類別建立 Web 要求和接收回應使用以 NTLM 的整合式 Windows 驗證的應用程式。  此變更可能影響配置使用整合式 Windows 驗證的 Web 伺服器和用戶端應用程式。  
  
## 概觀  
 驗證允許某些認證回應是通用的可重複使用整合式 Windows 的設計，這表示它們或轉寄。  如果這個特別設計功能是不需要的，則驗證通訊協定應該傳用特定目標的資訊和指引特定資訊。  服務可以提供擴充的保護確定認證回應包含 Service 特定的資訊 \(例如服務主要名稱 \(SPN\) \(SPN\)。  在認證交換的資訊，這個服務可以更妥善地防止可能不會正確地取得至認證回應的惡意用途。  
  
 在 <xref:System.Net> 的多個元件和 <xref:System.Net.Security> 命名空間表示呼叫的應用程式執行整合式 Windows 驗證。  本章節說明 System.Net 元件的變更加入至整合式 Windows 驗證其使用的延伸保護。  
  
## 變更  
 NTLM 驗證處理序使用整合式 Windows 驗證包括一個挑戰發行由目的電腦和送回給用戶端電腦。  在產生自己的電腦接收要求，驗證會失敗，除非連接是回送連接 IPv4 位址 127.0.0.1 \(例如，\)。  
  
 當存取在內部 Web 伺服器上執行的服務，通常會存取服務使用 URL 類似 http:\/\/contoso\/service 或 https:\/\/contoso\/service。  這個名稱「contoso」通常不是服務部署電腦的電腦名稱。  <xref:System.Net> 和相關命名空間支援使用 Active Directory， DNS，網路 I\/O 系統，本機電腦的主機檔案 \(例如通常 WINDOWS\\system32\\drivers\\etc\\hosts 等等\)，或本機電腦的 lmhosts 檔案 \(例如通常 WINDOWS\\system32\\drivers\\etc\\lmhosts 等等\)，將名稱解析成位址。  這個名稱「contoso」解析，以便將要求傳送至「contoso」傳送至適當伺服器電腦。  
  
 當設定為大型部署，也是很常見的事單一虛擬伺服器名稱要以用戶端應用程式和使用者沒有使用基礎電腦名稱的部署。  例如，您可能會在一個內部網路使用「contoso」server www.contoso.com，但是，。  這個名稱會在用戶端 Web 要求的主機標頭。  由 HTTP 通訊協定，主應用程式要求標頭的欄位指定所要求資源的網際網路主機和連接埠編號。  這個資訊給使用者或參考資源 \(通常是 HTTP URL 的原始 URI 取得。  在 .NET Framework 4 版中，此資訊可以使用新的 <xref:System.Net.HttpWebRequest.Host%2A> 屬性的用戶端也會設定為。  
  
 <xref:System.Net.AuthenticationManager> 類別控制 <xref:System.Net.WebRequest> 衍生項目類別和 <xref:System.Net.WebClient> 類別所使用的 Managed 驗證元件 \(「模組」\)。  <xref:System.Net.AuthenticationManager> 類別為應用程式提供在驗證期間使用的自訂 SPN 字串提供公開 <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=fullName> 物件的屬性，此索引以 URI 字串。  
  
 3.5 SP1 版本現在當 <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> 屬性未設定時，會預設為指定在 NTLM \(NT LAN Manager\) 驗證交換內 SPN 的要求 URL 中使用的主機名稱。  在要求 URL 中使用的主機名稱可能會與在用戶端要求中的 <xref:System.Net.HttpRequestHeader?displayProperty=fullName> 中指定的主機標頭不同。  在要求 URL 中使用的主機名稱可能會與伺服器的實際主機名稱、伺服器的電腦名稱、電腦的 IP 位址或回送位址不同。  在這些情況下，Windows 會使驗證要求失敗。  若要解決這個問題，我們需要通知 Windows 用來在用戶端要求 \(例如「contoso」的要求 URL 的主機名稱，\) 實際上是一個別名的本機電腦上。  
  
 具有伺服器應用程式的數個方法可以在此變更解決。  建議的方法是將用於要求 URL 的主機名稱至已註冊的 `BackConnectionHostNames` 索引鍵在伺服器上。  `BackConnectionHostNames` 登錄機碼通常用來將主機名稱為回送位址。  步驟如下所列。  
  
 若要指定對應到回送位址，並可在連接至本機電腦之網站的主機名稱，請依照下列步驟執行:  
  
 1.  依序按 \[開始\] 和 \[執行\]、輸入 regedit，然後按一下 \[確定\]。  
  
 2.  在登錄編輯程式，找出並按一下下列登錄機碼:  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0`  
  
 3.  以滑鼠右鍵按一下 MSV1\_0，指向新增，然後按一下新的字串值。  
  
 4.  輸入 `BackConnectionHostNames`，然後按 Enter。  
  
 5.  以滑鼠右鍵按一下 `BackConnectionHostNames`，然後按一下 修改。  
  
 6.  在數值資料的 方塊中，輸入主機名稱或主機名稱對於網站 \(用來要求 URL 的主機名稱\) 位於本機電腦，然後按一下 \[確定\]。  
  
 7.  中止登錄編輯程式，然後重新啟動 IISAdmin 服務並執行 IISReset。  
  
 安全性和工作是停用回送檢查，如中所 [http:\/\/support.microsoft.com\/kb\/896861](http://go.microsoft.com/fwlink/?LinkID=179657)述。  這會停用保護不受反映攻擊。  因此限制組別名給您預期機器實際使用的那些最好的做法。  
  
## 請參閱  
 <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=fullName>   
 <xref:System.Net.HttpRequestHeader?displayProperty=fullName>   
 <xref:System.Net.HttpWebRequest.Host%2A?displayProperty=fullName>