---
title: "重構和重新命名對話方塊 (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.RenameSymbol"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "符號, 重新命名"
  - "名稱, 變更符號"
  - "重新命名對話方塊"
ms.assetid: 001d2d81-9bb6-4e8e-ae3a-20c0daaa3959
redirect_url: https://msdn.microsoft.com/library/ckfya594(v=vs.140).aspx
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# 重構和重新命名對話方塊 (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

使用 Visual Basic 內建的 \[**重新命名**\] 對話方塊，可以重新命名程式碼中用於欄位、區域變數、方法、命名空間 \(Namespace\)、屬性和型別等符號的識別項。  以滑鼠右鍵按一下項目宣告，即可開啟 \[**重新命名**\] 對話方塊。  
  
 **新名稱**  
 指定程式碼項目的新名稱。  
  
 **Location**  
 識別您要執行重新命名作業時所要搜尋的命名空間。  
  
## 重新命名作業  
 視重新命名之項目的型別而定，\[**重新命名**\] 對話方塊所執行的重新命名作業會稍有不同。  
  
|項目型別|重新命名作業|  
|----------|------------|  
|類別|將所有宣告和所有使用的類別變更為新的名稱。  至於部分類別，重新命名作業會傳播到所有部分。|  
|欄位|將宣告和所有使用的欄位變更為新的名稱。|  
|區域變數|將變數的宣告及出現的地方變更為新名稱。|  
|方法|將方法的名稱和該方法的所有參考變更為新的名稱。|  
|命名空間|在宣告、所有的 `Imports` 陳述式 \(Statement\) 和所有的完整名稱中，將命名空間的名稱變更為新的名稱。|  
|屬性|將屬性的宣告及出現的地方變更為新名稱。|  
  
## 重構  
 為了提供完整的重構功能，Visual Basic 已經與 Developer Express Inc. 合作  取得重構支援。  如需如何下載此工具的詳細資訊和指示，請參閱 MSDN Visual Basic 開發人員中心上的[重整\!](http://go.microsoft.com/fwlink/?LinkId=155788) \(英文\)。  Refactor\!  支援 15 種以上的個別重構功能。  包括「重新排列參數」、「擷取方法」、「封裝欄位」和「建立多載」之類的作業。  
  
## 請參閱  
 [Using the Visual Basic Development Environment](../../../visual-basic/developing-apps/using-ide/using-the-visual-basic-development-environment.md)