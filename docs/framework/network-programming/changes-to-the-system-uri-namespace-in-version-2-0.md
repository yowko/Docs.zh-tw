---
title: "2.0 版之 System.Uri 命名空間的變更"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 906abbcbd3ec00e76d8c183f61828fb5135d9154
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a>2.0 版之 System.Uri 命名空間的變更
已對 <xref:System.Uri?displayProperty=nameWithType> 類別進行數項變更。 這些變更已修正不正確的行為、增強可用性和增強式安全性。  
  
## <a name="obsolete-and-deprecated-members"></a>已淘汰和已取代的成員  
 建構函式：  
  
-   所有具有 `dontEscape` 參數的建構函式。  
  
 方法:  
  
-   <xref:System.Uri.CheckSecurity%2A>  
  
-   <xref:System.Uri.Escape%2A>  
  
-   <xref:System.Uri.Canonicalize%2A>  
  
-   <xref:System.Uri.Parse%2A>  
  
-   <xref:System.Uri.IsReservedCharacter%2A>  
  
-   <xref:System.Uri.IsBadFileSystemCharacter%2A>  
  
-   <xref:System.Uri.IsExcludedCharacter%2A>  
  
-   <xref:System.Uri.EscapeString%2A>  
  
## <a name="changes"></a>變更  
  
-   針對已知沒有查詢部分的 URI 配置 (file、ftp 和其他項目)，一律會逸出 '?' 字元，而且它不是 <xref:System.Uri.Query%2A> 部分的開頭。  
  
-   針對隱含檔案 URI (形式為 "c:\directory\file@name.txt")，除非要求完整取消逸出，或 <xref:System.Uri.LocalPath%2A> 是 `true`，否則一律會逸出片段字元 ('#')。  
  
-   已移除 UNC 主機名稱支援；已採用用於呈現國際主機名稱的 IDN 規格。  
  
-   <xref:System.Uri.LocalPath%2A> 一律會傳回完整未逸出的字串。  
  
-   <xref:System.Uri.ToString%2A> 不會取消逸出已逸出的 '%'、'?' 或 '#' 字元。  
  
-   <xref:System.Uri.Equals%2A> 現在會在相等檢查時包含 <xref:System.Uri.Query%2A> 部分。  
  
-   運算子 "==" 和 "!=" 會覆寫並連結至 <xref:System.Uri.Equals%2A> 方法。  
  
-   <xref:System.Uri.IsLoopback%2A> 現在會產生一致的結果。  
  
-   URI "`file:///path`" 不再轉譯成 "file://path"。  
  
-   "#" 現在會辨識為主機名稱結束字元。 亦即，"http://consoto.com#fragment" 現在會轉換成 "http://contoso.com/#fragment"。  
  
-   已修正合併基底 URI 與片段時的 Bug。  
  
-   已修正 <xref:System.Uri.HostNameType%2A> 中的 Bug。  
  
-   已修正 NNTP 剖析中的 Bug。  
  
-   HTTP:contoso.com 形式的 URI 現在會擲回剖析例外狀況。  
  
-   Framework 可正確處理 URI 中的 userinfo。  
  
-   已修正 URI 路徑壓縮，因此中斷 URI 無法周遊檔案系統的根目錄。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Uri?displayProperty=nameWithType>
