---
title: 解譯網路追蹤
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 74ffa8a0ced264b29cd30cdcd1ca8f9a87c8c358
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="interpreting-network-tracing"></a>解譯網路追蹤
啟用網路追蹤時，您可以使用追蹤來擷取應用程式對各種 <xref:System.Net> 類別成員的呼叫。 這些呼叫的輸出可能類似下列範例。  
  
```  
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61  
```  
  
 在上述範例中，[588] 是目前執行緒的唯一識別碼。 (4357) 和 (4387) 時間戳記表示自應用程式啟動後所經歷的毫秒數。 時間戳記後面的資料會顯示應用程式進入和結束 **Socket.Send** 方法。 執行 **Send** 方法之物件的唯一識別碼是 33574638。 方法結束追蹤包含傳回值 (上例中為 61)。  
  
 網路追蹤可以擷取您的應用程式使用應用程式層級通訊協定，例如超文字傳輸通訊協定 (HTTP)，所傳送或接收的網路流量。 此資料可以擷取成文字或十六進位資料。 當您指定 **includehex** 作為 **tracemode** 屬性的值時，可以使用十六進位資料。 (如需此屬性的詳細資訊，請參閱[如何：設定網路追蹤](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)。)下列範例追蹤是使用 **includehex** 所產生。  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 若要省略十六進位資料，請指定 **protocolonly** 作為 **tracemode** 屬性的值。 當指定 **protocolonly** 時，下列範例會顯示追蹤。  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a>請參閱  
 [啟用網路追蹤](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [如何：設定網路追蹤](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)  
 [以 .NET Framework 進行網路追蹤](../../../docs/framework/network-programming/network-tracing.md)
