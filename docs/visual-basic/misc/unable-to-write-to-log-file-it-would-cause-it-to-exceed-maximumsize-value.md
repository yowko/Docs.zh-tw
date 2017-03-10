---
title: "無法寫入記錄檔，因為如果寫入，會使它超過 MaximumSize 值 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrApplicationLog_FileExceedsMaximumSize"
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# 無法寫入記錄檔，因為如果寫入，會使它超過 MaximumSize 值
<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 類別無法寫入記錄檔，因為：  
  
-   記錄檔大小 \(以位元組為單位\) 大於 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> 屬性的值  
  
     —且—  
  
-   <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> 屬性的值是 <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>。  
  
### 更正這個錯誤  
  
1.  封存現有的記錄檔並將其從電腦中移除，讓 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 物件可以建立新的記錄檔。  
  
2.  變更 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> 屬性的值以允許較大的記錄檔。  
  
3.  將 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> 屬性設定為 <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption>，以在記錄檔太大時，捨棄訊息而不發出警告。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 [My.Application.Log 物件](../../visual-basic/language-reference/objects/my-application-log-object.md)   
 [My.Log Object](../../visual-basic/language-reference/objects/my-log-object.md)