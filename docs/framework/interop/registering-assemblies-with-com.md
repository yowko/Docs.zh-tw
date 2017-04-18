---
title: "向 COM 註冊組件 | Microsoft Docs"
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
  - "COM Interop, 註冊組件"
  - "與 Unmanaged 程式碼的互通, 註冊組件"
  - "註冊組件"
  - "移除註冊組件"
ms.assetid: 87925795-a3ae-4833-b138-125413478551
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 向 COM 註冊組件
您可以執行一個名為[組件註冊工具 \(Regasm.exe\)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) 的命令列工具來註冊或移除註冊使用於 COM 的組件。  Regasm.exe 會將關於類別的資訊加入到系統登錄，讓 COM 用戶端可以無障礙地使用 .NET Framework 類別。  <xref:System.Runtime.InteropServices.RegistrationServices> 類別提供了同等的功能。  
  
 從 COM 用戶端啟動 Managed 元件之前，其必須註冊在 Windows 登錄中。  下表顯示 Regasm.exe 通常會加入至 Windows 登錄的機碼   \(000000 表示實際的 GUID 值\)。  
  
|GUID|描述|登錄機碼|  
|----------|--------|----------|  
|CLSID|類別識別項|HKEY\_CLASSES\_ROOT\\CLSID\\{000…000}|  
|IID|介面識別項|HKEY\_CLASSES\_ROOT\\Interface\\{000…000}|  
|LIBID|程式庫識別項|HKEY\_CLASSES\_ROOT\\TypeLib\\{000…000}|  
|ProgID|程式設計識別項|HKEY\_CLASSES\_ROOT\\000…000|  
  
 在 HKCR\\CLSID\\{0000...0000} 機碼之下，會將預設值設定為類別的 ProgID，並加入兩個新的已命名值 Class 和 Assembly。  Runtime 會從登錄中讀取組件值，然後將它傳遞給 Runtime 組件解析程式 \(Resolver\)。  組件解析程式會依據名稱和版本號碼這類組件資訊嘗試找出這個組件。  為了使組件解析程式找到組件，該組件必須在下列位置其中之一：  
  
-   全域組件快取 \(GAC\) \(必須為強式名稱的組件\)  
  
-   在應用程式目錄中。  從應用程式路徑載入的組件只能從那個應用程式才能夠存取  
  
-   指定的檔案路徑加上 Regasm.exe 的 **\/codebase** 選項  
  
 Regasm.exe 也會在 HKCR\\CLSID\\{0000...0000} 機碼之下建立 InProcServer32 機碼。  這個機碼的預設值會設定為內含 Common Language Runtime 的 DLL 名稱 \(Mscoree.dll\)。  
  
## 檢查登錄項目  
 COM Interop 提供了一個標準 Class Factory 實作，來建立任何 .NET Framework 類別的執行個體。  用戶端可以呼叫 Managed DLL 上的 **DllGetClassObject**，取得 Class Factory 並且建立物件，就像對任何其他 COM 元件一樣。  
  
 對於 `InprocServer32` 子機碼，對 Mscoree.dll 的參考在一個傳統 COM 型別程式庫位置表示 Common Language Runtime 建立 Managed 物件。  
  
## 請參閱  
 [將 .NET Framework 元件公開給 COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)   
 [如何：參考 COM 的 .NET 類型](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)   
 [Calling a .NET Object](http://msdn.microsoft.com/zh-tw/40c9626c-aea6-4bad-b8f0-c1de462efd33)   
 [Deploying an Application for COM Access](http://msdn.microsoft.com/zh-tw/fb63564c-c1b9-4655-a094-a235625882ce)