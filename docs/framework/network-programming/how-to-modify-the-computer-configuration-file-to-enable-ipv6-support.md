---
title: 作法：修改電腦組態檔以啟用 IPv6 支援
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: af6eb8a334108c988967a555024b524e27d40f58
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959070"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>作法：修改電腦組態檔以啟用 IPv6 支援
下列程式碼範例示範如何修改電腦組態檔 *machine.config* 來啟用 IPv6 支援。 *machine.config* 檔案是儲存在 Windows 安裝目錄中的 *%Windir%\Microsoft.NET\Framework* 資料夾下。 另外還有一個 *machine.config* 檔案，位於電腦上所安裝之每個 .NET Framework 版本的 *%Windir%\Microsoft.NET\Framework* 下的資料夾中 (例如，*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*)。  
  
 您也可以在應用程式的組態檔中進行這些設定，它的優先順序高於電腦組態檔。  
  
 如果是 .NET Framework 1.1 版及更早版本，[已啟用 IPv6]  組態參數的值會指定 <xref:System.Net.Dns?displayProperty=nameWithType> 類別的成員是否傳回 IPv6 位址。  
  
 如果是 .NET Framework 2.0 版及更新版本，如果 Windows 支援 IPv6，則 <xref:System.Net.Dns?displayProperty=nameWithType> 類別的所有成員 (例如，<xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> 方法) 將會傳回含有一個限制的 IPv6 位址。 <xref:System.Net.Dns?displayProperty=nameWithType> 類別的過時成員 (例如，<xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> 方法) 會讀取並辨識組態檔中的值。  
  
> [!NOTE]
> 如果是 .NET Framework 2.0 版及更新版本，預設會啟用 IPv6。 如果是 .NET Framework 1.1 版及更早版本，預設會停用 IPv6。  
  
## <a name="example"></a>範例  
  
```xml  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>   
    ……………  
    </settings>  
    ………………  
<system.net>  
```  
  
## <a name="see-also"></a>另請參閱

- [IPv6 定址](../../../docs/framework/network-programming/ipv6-addressing.md)
- [網路設定結構描述](../../../docs/framework/configure-apps/file-schema/network/index.md)
- [\<ipv6> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
