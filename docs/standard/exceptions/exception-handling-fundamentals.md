---
title: "例外狀況處理基礎觀念 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Common Language Runtime, 例外狀況"
  - "例外狀況, 範例"
  - "執行階段, 例外狀況"
ms.assetid: e865d48c-b862-4448-833e-09fcd48adf6b
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# 例外狀況處理基礎觀念
Common Language Runtime 根據例外狀況物件和程式碼保護區塊的概念，支援例外處理模型。  執行階段建立物件以在例外狀況發生時表示它。  您也可以藉著從適當基底例外狀況衍生類別，建立您自己的例外狀況類別。  
  
 所有使用執行階段的語言都以類似方式處理例外狀況。  每一個語言都使用 Try\/Catch\/Finally 結構化例外狀況處理。  本章節提供數個基本例外狀況處理的範例。  
  
## 在本節中  
 [HOW TO：使用 Try\/Catch 區塊攔截例外狀況](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)  
 說明如何使用 Try\/Catch 區塊來處理例外狀況。  
  
 [HOW TO：使用 Catch 區塊中的特定例外狀況](../../../docs/standard/exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)  
 說明如何攔截特定例外狀況。  
  
 [HOW TO：明確擲回例外狀況](../../../docs/standard/exceptions/how-to-explicitly-throw-exceptions.md)  
 說明擲回例外狀況的方法，以及先攔截再擲回例外狀況的方法。  
  
 [HOW TO：建立使用者定義的例外狀況](../../../docs/standard/exceptions/how-to-create-user-defined-exceptions.md)  
 說明如何建立您自己的例外狀況類別。  
  
 [使用使用者篩選的處理常式](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md)  
 說明如何設定篩選的例外狀況。  
  
 [HOW TO：使用 Finally 區塊](../../../docs/standard/exceptions/how-to-use-finally-blocks.md)  
 解釋如何在例外狀況區塊中使用 Finally 陳述式。  
  
## 相關章節  
 [例外狀況](../../../docs/standard/exceptions/index.md)  
 提供 Common Language Runtime 例外狀況的概觀。  
  
 [Exception 類別和屬性](../../../docs/standard/exceptions/exception-class-and-properties.md)  
 描述例外狀況物件的項目。