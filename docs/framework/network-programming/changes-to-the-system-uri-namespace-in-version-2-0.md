---
title: "2.0 版之 System.Uri 命名空間的變更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 2.0 版之 System.Uri 命名空間的變更
數個變更 <xref:System.Uri?displayProperty=fullName> 類別。  這些變更修正不正確的行為，引發的可用性，並增強安全性。  
  
## 過時並取代成員  
 建構函式:  
  
-   具有 `dontEscape`參數的任何建構函式。  
  
 方法:  
  
-   <xref:System.Uri.CheckSecurity%2A>  
  
-   <xref:System.Uri.Escape%2A>  
  
-   <xref:System.Uri.Canonicalize%2A>  
  
-   <xref:System.Uri.Parse%2A>  
  
-   <xref:System.Uri.IsReservedCharacter%2A>  
  
-   <xref:System.Uri.IsBadFileSystemCharacter%2A>  
  
-   <xref:System.Uri.IsExcludedCharacter%2A>  
  
-   <xref:System.Uri.EscapeString%2A>  
  
## 變更  
  
-   確定不會查詢組件 URI 配置的檔案 \(，、和其他\)， 「?」字元一律逸出和不會視為 <xref:System.Uri.Query%2A> 組件的開頭。  
  
-   隱含檔案的 URI \(格式為「c:\\directory\\file」\)， @name.txt 片段字元 \(「\#」\) 永遠是逸出字元，除非完整 unescaping 需求或 <xref:System.Uri.LocalPath%2A> 是 `true`。  
  
-   通用命名慣例 \(UNC\) 路徑已移除主機名稱支援，表示國際主機名稱的 IDN 規格的資料。  
  
-   <xref:System.Uri.LocalPath%2A> 一律會傳回完全逸出字串。  
  
-   <xref:System.Uri.ToString%2A> 不會逸出每個逸出字元" %」， 「? 」、「\#」字元。  
  
-   在<xref:System.Uri.Equals%2A> 相等檢查現在包含 <xref:System.Uri.Query%2A> 組件。  
  
-   運算子「\=\=」和「\! \=」與 <xref:System.Uri.Equals%2A> 覆寫並連接方法。  
  
-   <xref:System.Uri.IsLoopback%2A> 現在會產生不一致的結果。  
  
-   URI 「`file:///path`」不再轉譯為「file:\/\/path」。  
  
-   「\#」現在視為主機名稱結束字元。  也就是「http:\/\/consoto.com\#fragment」已轉換為「http:\/\/contoso.com\/\#fragment」。  
  
-   Bug，並在結合基底 URI 的片段中修正。  
  
-   在 <xref:System.Uri.HostNameType%2A> 的已修正 Bug。  
  
-   在剖析的 NNTP 的已修正 Bug。  
  
-   HTTP:contoso.com 格式的 URI 現在會擲回剖析例外狀況。  
  
-   Framework 正確處理 URI 中的 userinfo。  
  
-   URI 路徑壓縮是固定的，因此已中斷的 URI 不能周遊根上的檔案系統。  
  
## 請參閱  
 <xref:System.Uri?displayProperty=fullName>