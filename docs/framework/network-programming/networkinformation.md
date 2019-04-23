---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: 0820ad6a6d5000ef7ea575e856d883ba5325b1b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230976"
---
# <a name="networkinformation"></a>NetworkInformation
<xref:System.Net.NetworkInformation> 命名空間可讓您收集網路事件、變更、統計資料和屬性的相關資訊。 您也可以使用 <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> 類別，來判斷是否可連線至遠端主機。  
  
## <a name="network-availability-and-events"></a>網路可用性和事件  
 <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> 類別可讓您判斷網路位址或可用性是否已變更。 若要使用此類別，請建立事件處理常式來處理變更，並將它與 <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> 或 <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler> 建立關聯。 如需詳細資訊，請參閱[如何：偵測網路可用性和位址變更](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md)。  
  
## <a name="network-statistics-and-properties"></a>網路統計資料和屬性  
 您可以根據介面或通訊協定來收集網路統計資料和屬性。 <xref:System.Net.NetworkInformation.NetworkInterface>、<xref:System.Net.NetworkInformation.NetworkInterfaceType> 和 <xref:System.Net.NetworkInformation.PhysicalAddress> 類別提供特定網路介面的相關資訊，而 <xref:System.Net.NetworkInformation.IPInterfaceProperties>、<xref:System.Net.NetworkInformation.IPGlobalProperties>、<xref:System.Net.NetworkInformation.IPGlobalStatistics>、<xref:System.Net.NetworkInformation.TcpStatistics> 和 <xref:System.Net.NetworkInformation.UdpStatistics> 類別提供第 3 層和第 4 層封包的相關資訊。 如需詳細資訊，請參閱[如何：取得介面和通訊協定資訊](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md)。  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>判斷是否可以連線遠端主機  
 您可以使用 <xref:System.Net.NetworkInformation.Ping> 類別，判斷網路上的遠端主機是否啟動且可連線。 如需詳細資訊，請參閱[如何：Ping 主機](../../../docs/framework/network-programming/how-to-ping-a-host.md)。  
  
## <a name="see-also"></a>另請參閱

- [網路程式設計範例](../../../docs/framework/network-programming/network-programming-samples.md)
- [網路資訊技術範例](https://go.microsoft.com/fwlink/?LinkID=179564)
- [NetStat 工具技術範例](https://go.microsoft.com/fwlink/?LinkID=179562)
- [Ping 用戶端技術範例](https://go.microsoft.com/fwlink/?LinkID=179565)
