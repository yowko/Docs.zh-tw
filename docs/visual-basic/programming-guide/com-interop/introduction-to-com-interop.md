---
title: "Introduction to COM Interop (Visual Basic) | Microsoft Docs"
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
  - "interop assemblies"
  - "COM interop, about COM interop"
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Introduction to COM Interop (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

元件物件模型 \(COM\) 可讓物件將其功能公開給其他元件和主應用程式。  雖然多年來，COM 物件一直是 Windows 程式設計的基礎，不過針對 Common Language Runtime \(CLR\) 設計的應用程式提供許多優點。  
  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 應用程式最終將取代使用 COM 開發的應用程式。  在那之前，可能必須藉由 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 來使用或建立 COM 物件。  與 COM 的互通性 \(Interoperability\) 或是所謂的 *COM Interop*，可讓您使用現有的 COM 物件，同時又可依照自己的進度逐漸轉換到 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)]。  
  
 藉由使用 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 建立 COM 元件，即可使用免註冊的 COM Interop。  如此一來，當電腦上有安裝一個以上的 DLL 版本時，您就可以控制要啟用哪個 DLL 版本，並且讓使用者可以使用 XCOPY 或 FTP，將您的應用程式複製到他們電腦上應用程式可以執行的適當目錄。  如需詳細資訊，請參閱[免註冊的 COM Interop](../Topic/Registration-Free%20COM%20Interop.md)。  
  
## Managed 程式碼和資料  
 針對 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 開發的程式碼稱為「*Managed 程式碼*」\(Managed Code\)，其中包含由 CLR 使用的中繼資料 \(Metadata\)。  [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 應用程式所使用的資料就稱為「*Managed 資料*」\(Managed Data\)，因為執行階段會管理資料相關工作，例如配置和回收記憶體以及執行型別檢查。  根據預設，[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] 會使用 Managed 程式碼和資料，但您可使用 Interop 組件 \(將稍後在這個頁面中說明\) 來存取 COM 物件的 Unmanaged 程式碼和資料。  
  
## 組件  
 組件就是 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 應用程式最主要的建置組塊。  它是功能的集合，可建置、改寫以及部署為包含一個或多個檔案的單一實作單元。  每個組件都包含一份組件資訊清單 \(Assembly Manifest\)。  
  
## 型別程式庫和組件資訊清單  
 型別程式庫描述 COM 物件的特性，例如成員名稱和資料型別。  組件資訊清單則會針對 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 應用程式執行相同的功能。  組件資訊清單包含下列資訊：  
  
-   組件識別 \(Identity\)、版本、文化特性和數位簽章。  
  
-   組成組件實作的檔案。  
  
-   構成組件的型別和資源。  其中包含從組件匯出的型別和資源。  
  
-   與其他組件的編譯時期相依性。  
  
-   正常執行組件所需的使用權限。  
  
 如需組件和組件資訊清單的詳細資訊，請參閱[組件和全域組件快取](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)。  
  
### 匯入和匯出型別程式庫  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 包含公用程式 Tlbimp，可讓您將型別程式庫的資訊匯入 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 應用程式。  您可以使用 Tlbexp 公用程式來從組件產生型別程式庫。  
  
 如需 Tlbimp 和 Tlbexp 的詳細資訊，請參閱[Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md) 和[Tlbexp.exe \(Type Library Exporter\)](../Topic/Tlbexp.exe%20\(Type%20Library%20Exporter\).md)。  
  
## Interop 組件  
 Interop 組件是用來當做 Managed 和 Unmanaged 程式碼之間連接橋樑的 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 組件，會將 COM 物件成員對應至對等的 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] Managed 成員。  [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] 建立的 Interop 組件可處理許多使用 COM 物件的細節，例如互通性封送處理 \(Marshaling\)。  
  
## 互通性封送處理  
 所有 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 應用程式都共用一組一般型別，可讓物件在無論使用何種程式語言的情況下互通。  COM 物件的參數和傳回值有時使用的資料型別與在 Managed 程式碼中使用的不同。  「*互通性封送處理*」\(Interoperability Marshaling\) 是參數和傳回值在 COM 物件之間來回移動時，將其封裝 \(Package\) 為對等資料型別的處理過程。  如需詳細資訊，請參閱 [Interop 封送處理](../Topic/Interop%20Marshaling.md)。  
  
## 請參閱  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [與 Unmanaged 程式碼互通](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)   
 [組件和全域組件快取](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)   
 [Tlbexp.exe \(Type Library Exporter\)](../Topic/Tlbexp.exe%20\(Type%20Library%20Exporter\).md)   
 [Interop 封送處理](../Topic/Interop%20Marshaling.md)   
 [免註冊的 COM Interop](../Topic/Registration-Free%20COM%20Interop.md)