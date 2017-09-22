---
title: "以 .NET Framework 進行網路追蹤"
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
helpviewer_keywords:
- debugging [.NET Framework], network tracing
- methods, network tracing
- Networking
- trace enabled debugging
- network tracing, about network tracing
- network tracing
- network, network tracing
- traffic tracing
- tracing [.NET Framework], network
- deploying applications [.NET Framework], network traffic
- capturing network traffic
- Internet, network tracing
- Network Resources
- output, network tracing
- method invocations
ms.assetid: e993b7c3-087f-45d8-9c02-9dded936d804
caps.latest.revision: 9
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c8c915edee4fe23b1718f4820eff9998fa9e5836
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="network-tracing-in-the-net-framework"></a>以 .NET Framework 進行網路追蹤
針對方法叫用及 Managed 應用程式所產生的網路流量，.NET Framework 中的網路追蹤能提供對這些相關資訊的存取。 若要為開發中的應用程式進行偵錯，以及分析已部署的應用程式，此功能會非常有用。 您可以自訂網路追蹤所提供的輸出，在程式開發時期和實際執行環境中支援不同的使用案例。  
  
 若要啟用 .NET Framework 中的網路追蹤，您必須為追蹤輸出選取一個目的地，並在應用程式或電腦組態檔中加入網路追蹤組態設定。 如需組態檔和其使用方式的描述，請參閱[組態檔](../../../docs/framework/configure-apps/index.md)。 如需如何啟用網路追蹤的資訊，請參閱[啟用網路追蹤](../../../docs/framework/network-programming/enabling-network-tracing.md)。 如需必須新增至組態檔之設定的資訊，請參閱[如何：設定網路追蹤](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)。  
  
 啟用追蹤之後，您就可以擷取 **System.Net** 類別所輸出的追蹤資訊。 可產生追蹤資訊的網路類別成員在它們的 .NET Framework 類別庫文件的＜備註＞一節中會包含下面附註：  
  
> [!NOTE]
>  在應用程式中啟用網路追蹤時，這個成員會輸出追蹤資訊。 如需詳細資訊，請參閱＜網路追蹤＞。  
  
## <a name="see-also"></a>另請參閱  
 [啟用網路追蹤](../../../docs/framework/network-programming/enabling-network-tracing.md)   
 [如何：設定網路追蹤](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)   
 [解譯網路追蹤](../../../docs/framework/network-programming/interpreting-network-tracing.md)   
 [檢測和追蹤的簡介](http://msdn.microsoft.com/en-us/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)

