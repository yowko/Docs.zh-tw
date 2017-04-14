---
title: "封送處理字串 | Microsoft Docs"
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
  - "資料封送處理, 平台叫用"
  - "資料封送處理, 範例"
  - "資料封送處理, 字串"
  - "封送處理, 平台叫用"
  - "封送處理, 範例"
  - "封送處理字串"
  - "平台叫用, 封送處理資料"
  - "範例應用程式 [.NET Framework], 封送處理字串"
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 封送處理字串
如果需要的話，平台叫用會複製字串參數，將它們從 .NET Framework 格式 \(Unicode\) 轉換成 Unmanaged 格式 \(ANSI\)。  因為 Managed 字串是不變的，所以當函式傳回時，平台叫用並不會從 Unmanaged 記憶體中將 Managed 字串複製回 Managed 記憶體。  
  
 下表列出字串的封送處理選項、說明其用法，並提供對應之 .NET Framework 範例的連結。  
  
|字串|描述|範例|  
|--------|--------|--------|  
|傳值方式|將字串當成 In 參數傳遞|[MsgBox](../../../docs/framework/interop/msgbox-sample.md)|  
|做為結果|從 Unmanaged 程式碼傳回字串|[字串](http://msdn.microsoft.com/zh-tw/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|傳址方式|使用 <xref:System.Text.StringBuilder>，將字串當成 In\/Out 參數傳遞|[Buffers](http://msdn.microsoft.com/zh-tw/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|在結構中 \- 傳值方式|傳遞結構中的字串 \(結構是 In 參數\)|[Structs](http://msdn.microsoft.com/zh-tw/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|在結構中 \- 傳址方式 **\(char\*\)**|傳遞結構中的字串 \(結構是 In\/Out 參數\)。  Unmanaged 函式預期是字元緩衝區的指標，而緩衝區大小是結構的成員|[字串](http://msdn.microsoft.com/zh-tw/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|在結構中 \- 傳址方式 **\(char\[\]\)**|傳遞結構中的字串 \(結構是 In\/Out 參數\)。  Unmanaged 函式預期是內嵌字元緩衝區|[OSInfo](http://msdn.microsoft.com/zh-tw/69d89067-507b-41fe-859d-30bf3ff29455)|  
|在類別中 \- 傳值方式 **\(char\*\)**|傳遞類別中的字串 \(類別是 In\/Out 參數\)。  Unmanaged 函式預期字元緩衝區的指標|[OpenFileDlg](http://msdn.microsoft.com/zh-tw/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|在類別中 \- 傳值方式 **\(char\[\]\)**|傳遞類別中的字串 \(類別是 In\/Out 參數\)。  Unmanaged 函式預期是內嵌字元緩衝區|[OSInfo](http://msdn.microsoft.com/zh-tw/69d89067-507b-41fe-859d-30bf3ff29455)|  
|做為傳值字串的陣列|建立以傳值方式傳遞的字串陣列|[陣列](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|做為含有傳值字串的結構陣列|建立含有字串的結構陣列，而且陣列是以傳值方式傳遞|[陣列](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## 請參閱  
 [使用平台叫用封送處理資料](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)   
 [Platform Invoke Data Types](http://msdn.microsoft.com/zh-tw/16014d9f-d6bd-481e-83f0-df11377c550f)   
 [封送處理類別、結構和等位](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md)   
 [Marshaling Arrays of Types](http://msdn.microsoft.com/zh-tw/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)   
 [Miscellaneous Marshaling Samples](http://msdn.microsoft.com/zh-tw/a915c948-54e9-4d0f-a525-95a77fd8ed70)