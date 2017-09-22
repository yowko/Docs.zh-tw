---
title: "使用組件設計程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
caps.latest.revision: 18
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 368021062a3ad49d2c63f92797c59b8c0f1cddfc
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 使用組件設計程式
組件是 .NET Framework 應用程式的建置組塊；它們構成部署、版本控制、重複使用、啟動過程 \(Activation\) 範圍設定和安全性使用權限的基本單位。  組件為 Common Language Runtime 提供了讓它察知型別實作所需的資訊。  組件是建置來共同運作及構成一個功能邏輯單位的型別和資源的集合。  對於執行階段而言，型別不會存在於組件的內容以外。  
  
 本節將說明如何建立模組、從模組建立組件、建立金鑰組並使用強式名稱簽署組件，並將組件安裝至全域組件快取。  此外，本節將說明如何使用 [MSIL 反組譯工具 \(Ildasm.exe\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢視組件資訊清單 \(Assembly Manifest\) 資訊。  
  
> [!NOTE]
>  從 .NET Framework 2.0 版開始，如果使用比目前載入之執行階段版本還要高的 .NET Framework 版本來編譯組件，則執行階段將不會載入這個組件。  這種情形適用於版本號碼的主要和次要元件組合。  
  
## 在本節中  
 [建立組件](../../../docs/framework/app-domains/create-assemblies.md)  
 提供單一檔案或多檔案組件的概觀。  
  
 [組件名稱](../../../docs/framework/app-domains/assembly-names.md)  
 提供組件命名的概觀。  
  
 [如何：決定組件的完整名稱](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 描述如何判斷組件的完整名稱。  
  
 [在完全信任環境下執行內部網路應用程式](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 描述如何針對內部網路共用上的完全信任組件指定舊版安全性原則。  
  
 [組件位置](../../../docs/framework/app-domains/assembly-location.md)  
 提供找出組件位置的概觀。  
  
 [如何：建置單一檔案組件](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 說明如何建立單一檔案組件。  
  
 [多檔案組件](../../../docs/framework/app-domains/multifile-assemblies.md)  
 描述建立多檔案組件的理由。  
  
 [如何：建置多檔案組件](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 說明如何建立多檔案組件。  
  
 [設定組件屬性](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 說明組件屬性和如何設定組件屬性。  
  
 [建立和使用強式名稱的組件](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 描述使用強式名稱簽署組件的方法和原因，並提供 HOW TO 主題。  
  
 [延遲簽署組件](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 說明如何延遲簽署組件。  
  
 [使用組件和全域組件快取](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 描述將組件加入到全域組件快取的方法和原因，並提供 HOW TO 主題。  
  
 [如何：檢視組件內容](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 說明如何使用 MSIL 反組譯工具 \(Ildasm.exe\) 來檢視組件內容。  
  
 [Common Language Runtime 中的類型轉送](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 說明如何使用型別轉送，將某個型別移到另一個組件，而不需中斷現有的應用程式。  
  
## 參考  
 <xref:System.Reflection.Assembly>  
 表示組件的 .NET Framework 類別。  
  
## 相關章節  
 [如何：從組件中取得類型和成員資訊](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 說明如何使用程式從組件取得型別和其他資訊。  
  
 [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 提供 Common Language Runtime 組件概觀。  
  
 [組件版本控制](../../../docs/framework/app-domains/assembly-versioning.md)  
 提供組件繫結以及 <xref:System.Reflection.AssemblyVersionAttribute> 和 <xref:System.Reflection.AssemblyInformationalVersionAttribute> 屬性的概觀。  
  
 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 說明執行階段如何決定用來滿足繫結要求的組件。  
  
 [反映](../../../docs/framework/reflection-and-codedom/reflection.md)  
 描述如何使用「反映」類別，以取得組件的相關資訊。

