---
title: "解譯網路追蹤 | Microsoft Docs"
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
helpviewer_keywords: 
  - "TraceMode 屬性"
  - "十六進位資料，網路追蹤輸出"
  - "網路追蹤，分析"
  - "protocolonly"
  - "文字，網路追蹤輸出"
  - "includehex"
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 解譯網路追蹤
當網路追蹤啟用時，您可以使用追蹤擷取您的應用程式會對各種 <xref:System.Net> 類別成員的呼叫。  從這些呼叫的輸出可能類似下列範例。  
  
```  
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61  
```  
  
 在上述範例中， 為 588 目前執行緒的唯一識別項。  \(4357\) 和 \(4387\) 是運算式以來所經過的毫秒數時間戳記，自應用程式啟動。  遵循時間戳記的資料顯示進入及結束方法 **Socket.Send**的應用程式。  執行 **傳送** 方法的物件具有 33574638 做為它的唯一識別項。  方法也會結束追蹤包括傳回值 61 \(在上述範例中\)。  
  
 網路追蹤可能擷取傳送或由您的應用程式能夠使用應用程式層級通訊協定 \(例如超文字傳輸通訊協定 \(HTTPS\) 的網路流量 \(HTTP\)。  這項資料，可以選擇性地，擷取為文字，而十六進位資料。  當您指定 **includehex** **tracemode** 做為屬性的值時，十六進位資料的功能。  \(如需此屬性的詳細資訊，請參閱 [HOW TO:設定網路追蹤](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)\)。使用 **includehex**，下列範例會產生追蹤。  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 若要省略十六進位資料，請指定 **protocolonly** 做為值。 **tracemode** 屬性。  當 **protocolonly** 指定時，下列範例會顯示追蹤。  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## 請參閱  
 [啟用網路追蹤](../../../docs/framework/network-programming/enabling-network-tracing.md)   
 [HOW TO:設定網路追蹤](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)   
 [以 .NET Framework 進行網路追蹤](../../../docs/framework/network-programming/network-tracing.md)