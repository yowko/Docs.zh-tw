---
title: "如何：建立 COM 包裝函式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "COM, 包裝函式建立"
  - "COM, 包裝函式 Visual Studio"
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：建立 COM 包裝函式
您可以使用 [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] 功能或 .NET Framework 工具 Tlbimp.exe 和 Regasm.exe 來建立元件物件模型 \(Component Object Model，COM\) 包裝函式。  這兩種方法會產生兩種類型的 COM 包裝函式：  
  
-   型別程式庫中的[執行階段可呼叫包裝函式](../../../docs/framework/interop/runtime-callable-wrapper.md)，會以 Managed 程式碼執行 COM 物件。  
  
-   具有需要之登錄設定的 [COM 可呼叫包裝函式](../../../docs/framework/interop/com-callable-wrapper.md)，會在原生應用程式中執行 Managed 物件。  
  
 在 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 中，您可以將 COM 包裝函式加入成為專案的參考。  
  
## 在 Managed 應用程式中包裝 COM 物件  
  
#### 使用 Visual Studio 建立執行階段可呼叫包裝函式  
  
1.  開啟您的 Managed 應用程式的專案。  
  
2.  在 \[**專案**\] 功能表上，按一下 \[**顯示所有檔案**\]。  
  
3.  在 \[**專案**\] 功能表上，按一下 \[**加入參考**\]。  
  
4.  在 \[加入參考\] 對話方塊中，按一下 \[**COM**\] 索引標籤，選取您所要使用的元件，並按一下 \[**確定**\]。  
  
     在 \[**方案總管**\] 中，注意 COM 元件已經加入到專案的 \[參考\] 資料夾中。  
  
 現在您可以撰寫程式碼以存取 COM 物件。  您可以從宣告物件開始，例如運用 [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] 的 `Imports` 陳述式，或是 [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)] 的 `Using` 陳述式。  
  
> [!NOTE]
>  如果您想要開發 Microsoft Office 元件，請先安裝可從 Microsoft 下載中心取得的 [Microsoft Office 主要 Interop 組件](http://go.microsoft.com/fwlink/?LinkId=50479) \(PIA\)。  在步驟 4 中，選取您所需要之 Office 產品的最新可用物件程式庫，例如 \[**Microsoft Word 11.0 物件程式庫**\]。  [](http://msdn.microsoft.com/zh-tw/c9d2a8b9-69df-4c0b-90ca-4d85bae063c4)  
  
#### 使用 .NET Framework 工具建立執行階段可呼叫包裝函式  
  
-   執行[Tlbimp.exe \(Type Library Importer\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) 工具。  
  
 這項工具所建立的組件，會包含由原始型別程式庫中所定義之型別的執行階段中繼資料。  
  
## 在原生應用程式中包裝 Managed 物件  
  
#### 使用 Visual Studio 建立 COM 可呼叫包裝函式  
  
1.  建立您要在機器碼中執行之 Managed 類別 \(Class\) 的類別庫 \(Class Library\) 專案。  此類別必須具有預設的建構函式 \(Constructor\)。  
  
     確認您在 AssemblyInfo 檔案中，擁有組件的完整四部分版本號碼。  這個號碼對於在 Windows 登錄中維護版本控制是必要的。  如需版本號碼的詳細資訊，請參閱[組件版本控制](../../../docs/framework/app-domains/assembly-versioning.md)。  
  
2.  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
3.  按一下 \[**編譯**\] 索引標籤。  
  
4.  選取 \[**註冊 COM Interop**\] 核取方塊。  
  
 當您建置 \(Build\) 專案時，組件便會為 COM Interop 自動註冊。  如果您是在 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 中建置原生應用程式，即可在 \[**專案**\] 功能表上按一下 \[**加入參考**\] 以使用組件。  
  
#### 使用 .NET Framework 工具建立 COM 可呼叫包裝函式  
  
-   執行[Regasm.exe \(Assembly Registration Tool\)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) 工具。  
  
 這項工具會讀取組件中繼資料，並將需要的項目加入登錄。  因此，COM 用戶端便能無障礙地建立 .NET Framework 類別。  您可以使用與原生 COM 類別相同的方式來使用組件。  
  
 您可以對位於任何目錄中的組件執行 Regasm.exe，然後再執行[Gacutil.exe \(Global Assembly Cache Tool\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) 將其移動到全域組件快取中。  移動組件並不會使位置登錄項目無效，因為只要在其他位置找不到組件，就永遠都會對全域組件快取進行檢查。  
  
## 請參閱  
 [執行階段可呼叫包裝函式](../../../docs/framework/interop/runtime-callable-wrapper.md)   
 [COM 可呼叫包裝函式](../../../docs/framework/interop/com-callable-wrapper.md)