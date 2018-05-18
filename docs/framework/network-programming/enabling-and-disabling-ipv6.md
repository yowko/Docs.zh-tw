---
title: 啟用和停用 IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b018d646816bda96945a440a890da20b81b1cbbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="enabling-and-disabling-ipv6"></a>啟用和停用 IPv6
若要使用 IPv6 通訊協定，請確定您執行的作業系統版本支援 IPv6，並確認已正確設定作業系統和網路類別。  
  
## <a name="configuration-steps"></a>設定步驟  
 下表列出各種組態  
  
|作業系統是否啟用 IPv6？|網路類別是否啟用 IPv6？|描述|  
|-------------------------------------|---------------------------------------|-----------------|  
|否|否|可以剖析 IPv6 位址。|  
|否|[是]|可以剖析 IPv6 位址。|  
|[是]|否|使用未標記為已淘汰的名稱解析方法，可以剖析 IPv6 位址並解析 IPv6 位址。|  
|[是]|[是]|使用所有的方法，包括標記為已淘汰的在內，可以剖析和解析 IPv6 位址。|  
  
 請注意，若要在 System.Net 命名空間中啟用所有類別的 IPv6 支援，您必須修改電腦組態檔或應用程式的組態檔。 應用程式組態檔的優先順序高於電腦組態檔。  
  
 如需如何修改電腦組態檔 *machine.config* 的範例，以啟用 Ipv6 支援，請參閱[如何：修改電腦組態檔以啟用 Ipv6 支援](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)。 此外，確定作業系統已啟用 IPv6 支援。  
  
 .NET Framework 在組態檔中設定的組態參數，如下所示：  
  
```xml  
<system.net>…  
    <settings>…  
        <ipv6 enabled="true"/>…  
    </settings>…  
</system.net>  
```  
  
 如果是 .NET Framework 1.1 版及更早版本，[已啟用 IPv6] 組態參數的值會指定 <xref:System.Net.Dns?displayProperty=nameWithType> 類別的成員是否傳回 IPv6 位址。  
  
 針對 .NET Framework 2.0 版及更新版本，如果 Windows 支援 IPv6，則 <xref:System.Net.Dns?displayProperty=nameWithType> 類別的成員 (例如，<xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> 方法) 將會傳回含有一個限制的 IPv6 位址。 DNS <xref:System.Net.Dns?displayProperty=nameWithType> 已淘汰的成員 (例如，<xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> 方法) 會讀取並辨識組態檔中啟用 ipv6 設定的值。  
  
## <a name="see-also"></a>請參閱  
 [網際網路通訊協定第 6 版](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [通訊端](../../../docs/framework/network-programming/sockets.md)  
 [網路設定結構描述](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [\<ipv6> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
