---
title: "使用序列化繫結器 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 使用序列化繫結器
此範例示範如何使用 <xref:System.Runtime.Serialization.SerializationBinder> 變更序列化時一般類型的版本。  
  
## 示範  
 <xref:System.Runtime.Serialization.SerializationBinder>,<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## 討論  
 此範例示範目標為不同版本之 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的兩個實體如何使用 Binary Formatter 和序列化繫結器進行通訊。  
  
 此範例的開發已經使用 .NET Remoting 完成。此範例由目標為 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 且實作具有一般類型之合約的一個伺服器，以及兩個不同的用戶端 \(一個目標為 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] 而另一個目標為 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]\) 所組成。  
  
 伺服器會將 <xref:System.Runtime.Serialization.SerializationBinder> 附加到 Binary Formatter 以便能夠根據序列化變更型別的版本，因此，兩個用戶端都可以正確還原序列化這些型別。  
  
#### 若要設定、建立及執行範例  
  
1.  若要執行用戶端，以滑鼠右鍵按一下 SBGenericsVTS 方案 \(6 個專案\)，然後選取 \[**屬性**\]。  
  
2.  選取 \[**通用屬性**\] 中的 \[**啟始專案**\]，然後選取 \[**多個啟始專案**\]。  
  
3.  先選取 \[**Server**\]，然後再選取 \[**Client20**\] 和 \[**Client40**\]。針對這三個專案選取 \[**開始**\] 動作，然後將其餘的專案設定為 \[**無**\]。  
  
4.  按一下 \[**確定**\]，然後按下 F5 以執行範例。