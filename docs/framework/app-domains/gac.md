---
title: "全域組件快取"
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
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
caps.latest.revision: 13
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bad9e339896b0d62dce75a4044b18f3ae6a69332
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 全域組件快取
安裝 Common Language Runtime 的每一部電腦都有一個稱為全域組件快取之整部電腦通用的程式碼快取。  全域組件快取會儲存要專門指定給電腦上一些應用程式共用的組件。  
  
 您應該在需要的時候才將組件安裝到全域組件快取中以便共用它們。  基本的指導原則是，除非明確需要共用組件，否則應使組件相依性保持私用 \(Private\)，並將組件置於應用程式目錄中。  此外，您不需要將組件安裝到全域組件快取中來使它們能讓 COM Interop 或 Unmanaged 程式碼存取。  
  
> [!NOTE]
>  在有些案例中，您絕對不能將組件安裝到全域組件快取中。  如果您將構成應用程式的某一個組件置於全域組件快取中，那麼就再也不能使用複製應用程式目錄的 **xcopy** 命令來複製或安裝應用程式。  您還必須移動全域組件快取中的組件。  
  
 有兩種方式可以將組件部署到全域組件快取中：  
  
-   使用為配合全域組件快取運作所設計的安裝程式。  這是將組件安裝到全域組件快取所慣用的選項。  
  
-   使用一種由 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 所提供，稱為[全域組件快取工具 \(Gacutil.exe\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) 的開發人員工具。  
  
    > [!NOTE]
    >  在部署案例中，請使用 Windows Installer 將組件安裝到全域組件快取中。  全域組件快取工具只可以使用於開發案例中，因為它不提供使用 Windows Installer 時所提供的組件參考計數和其他功能。  
  
 從.NET Framework 4 開始，全域組件快取的預設位置是 **%windir% \\ Microsoft.NET \\組件**。  在舊版的 .NET Framework 中，預設位置為 **%windir% \\組件**。  
  
 系統管理員通常會使用存取控制清單 \(ACL\) 來控制撰寫和執行存取，以保護 systemroot 目錄。  由於全域組件快取安裝在 systemroot 目錄的子目錄中，因此它繼承了該目錄的 ACL。  建議使用者只有在具備系統管理員權限時，才能從全域組件快取刪除檔案。  
  
 部署在全域組件快取中的組件必須具有強式名稱。  當組件加入到全域組件快取時，會對構成該組件的所有檔案進行完整性檢查。  快取會執行這些完整性檢查以確保組件未遭竄改 \(例如，檔案已經變更，但資訊清單並未反映變更\)。  
  
## 請參閱  
 [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)   
 [使用組件和全域組件快取](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)   
 [強式名稱的組件](../../../docs/framework/app-domains/strong-named-assemblies.md)

