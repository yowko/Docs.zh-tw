---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: bc0604fd33d06521727c9aa0302ed313d8a2305f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428227"
---
# <a name="networkinformation"></a>NetworkInformation
<xref:System.Net.NetworkInformation> 命名空間可讓您收集網路事件、變更、統計資料和屬性的相關資訊。 您也可以使用 <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> 類別，來判斷是否可連線至遠端主機。  
  
## <a name="network-availability-and-events"></a>網路可用性和事件  
 <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> 類別可讓您判斷網路位址或可用性是否已變更。 若要使用此類別，請建立事件處理常式來處理變更，並將它與 <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> 或 <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler> 建立關聯。 如需詳細資訊，請參閱[如何：偵測網路可用性和位址變更](how-to-detect-network-availability-and-address-changes.md)。  
  
## <a name="network-statistics-and-properties"></a>網路統計資料和屬性  
 您可以根據介面或通訊協定來收集網路統計資料和屬性。 <xref:System.Net.NetworkInformation.NetworkInterface>、<xref:System.Net.NetworkInformation.NetworkInterfaceType> 和 <xref:System.Net.NetworkInformation.PhysicalAddress> 類別提供特定網路介面的相關資訊，而 <xref:System.Net.NetworkInformation.IPInterfaceProperties>、<xref:System.Net.NetworkInformation.IPGlobalProperties>、<xref:System.Net.NetworkInformation.IPGlobalStatistics>、<xref:System.Net.NetworkInformation.TcpStatistics> 和 <xref:System.Net.NetworkInformation.UdpStatistics> 類別提供第 3 層和第 4 層封包的相關資訊。 如需詳細資訊，請參閱[如何：取得介面和通訊協定資訊](how-to-get-interface-and-protocol-information.md)。  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>判斷是否可以連線遠端主機  
 您可以使用 <xref:System.Net.NetworkInformation.Ping> 類別，判斷網路上的遠端主機是否啟動且可連線。 如需詳細資訊，請參閱[如何：Ping 主機](how-to-ping-a-host.md)。  
  
## <a name="see-also"></a>請參閱

- [網路程式設計範例](network-programming-samples.md)

<!-- to-do: review sample links
- [Network Information Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Network%20Information)
- [NetStat Tool Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=NetStat%20Tool)
- [Ping Client Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Ping%20Client)
-->
