---
title: WCF 及國際化網域名稱
ms.date: 03/30/2017
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
ms.openlocfilehash: c166f497117314dd8cea3b04b9b1072203374c52
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112602"
---
# <a name="wcf-and-internationalized-domain-names"></a>WCF 及國際化網域名稱
已加入支援，以允許具有國際化網域名稱 (IDN) 的 WCF 服務。 國際化網域名稱是包含非 ASCII 字元的網域名稱。 這項支援包括兩種能力，即裝載具有 IDN 名稱之 WCF 服務，以及裝載對具有 IDN 名稱之 Web 服務進行交談的 WCF 用戶端。  
  
## <a name="systemuri-and-idn"></a>System.Uri 和 IDN  
 <xref:System.Uri> 有兩個屬性<xref:System.Uri.Host%2A>和<xref:System.Uri.DnsSafeHost%2A>。 這些屬性包含 Unicode 或 Punycode 值，因 IDN 組態設定而異。  
  
 使用下列 XML 以在應用程式組態檔中啟用 IDN  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 \<Idn > 項目包含啟用的屬性，可以設定為下列值之一：  
  
1.  「 無 」  
  
2.  "AllExceptIntranet"  
  
3.  [全部]  
  
 當 IDN 設定設定為 「 無 」 時，Uri.Host 或 Uri.DnsSafeHost 並未不執行任何轉換。 當 IDN 設定設為"All"，uri。主機會維持 Unicode 和 uri。DnsSafeHost 會轉換為 Punycode。 當 IDN 設定設為"AllExceptIntranet"，uri。DnsSafeHost 網際網路位址轉換為 Punycode，對內部網路位址則保持為 Unicode。 這個設定對正確解析 DNS 名稱很重要。 請注意，Windows 8 和較新的版本不需要進行這個設定。  
  
> [!WARNING]
>  永遠不要使用 Punycode 將位址寫成硬式編碼。 WCF 會根據您套用的組態設定來為您進行轉換。  
  
> [!WARNING]
>  將 Unicode 字元加入至 applicationHost.exe.config，請使用 UTF-8 編碼儲存檔案。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Uri?displayProperty=nameWithType>
