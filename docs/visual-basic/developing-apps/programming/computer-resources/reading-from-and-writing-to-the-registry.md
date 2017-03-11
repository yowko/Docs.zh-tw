---
title: "Reading from and Writing to the Registry (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Computer.Registry object, tasks"
  - "registry, writing to"
  - "registry, reading"
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Reading from and Writing to the Registry (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

本主題將說明工作和概念與登錄相關的主題。  
  
 在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中設計程式時，您可以選擇藉由 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 提供的函式或藉由 .NET Framework 的登錄類別來存取登錄。  登錄裝載了作業系統資訊以及電腦所裝載的應用程式資訊。  使用登錄會允許不適當存取系統資源或受保護的資訊，因此可能危害安全性。  
  
## 在本節中  
 [How to: Create a Registry Key and Set Its Value](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 說明如何使用`CreateSubKey`和`SetValue`的方法`My.Computer.Registry`來建立登錄機碼，並設定其值的物件。  
  
 [How to: Read a Value from a Registry Key](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 說明如何使用`GetValue`方法的`My.Computer.Registry`登錄機碼讀取值的物件。  
  
 [How to: Delete a Registry Key](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 說明如何使用`DeleteSubKey`方法的`My.Computer.Registry.CurrentUser`刪除登錄機碼的屬性。  
  
 [使用 Microsoft.Win32 命名空間讀取和寫入登錄](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 說明如何使用`Registry`和`RegistryKey`類別的[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)]存取登錄。  
  
 [Security and the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 討論有關登錄的安全性問題。  
  
## 相關章節  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 列出並說明 `My.Computer.Registry` 物件的成員。  
  
 <xref:Microsoft.Win32.Registry>  
 呈現 `Registry` 類別的概觀，以及個別機碼和成員的連結。