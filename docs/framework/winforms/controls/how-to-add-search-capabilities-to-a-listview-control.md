---
title: "如何：將搜尋能力加入至 ListView 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "清單檢視, 啟用搜尋"
  - "清單, 啟用搜尋"
  - "ListView 控制項 [Windows Form], 加入搜尋功能"
  - "搜尋, 將搜尋功能加入到 ListView 控制項"
ms.assetid: 557782d9-b705-4bab-b496-9938afddac82
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：將搜尋能力加入至 ListView 控制項
通常在 <xref:System.Windows.Forms.ListView> 控制項中使用大型的項目清單時，您會想要為使用者提供搜尋功能。  <xref:System.Windows.Forms.ListView> 控制項以兩種不同方式提供這項功能：文字比對和位置搜尋。  
  
 如果知道搜尋字串以及選擇性的開始和結束索引，就可以透過 <xref:System.Windows.Forms.ListView.FindItemWithText%2A> 方法在清單或詳細資料檢視中的 <xref:System.Windows.Forms.ListView> 上執行文字搜尋。  相反地，如果有一組 X 和 Y 軸座標及搜尋的方向，就可以透過 <xref:System.Windows.Forms.ListView.FindNearestItem%2A> 方法在圖示或並排顯示中尋找 <xref:System.Windows.Forms.ListView> 內的物件。  
  
### 若要使用文字尋找項目  
  
1.  建立 <xref:System.Windows.Forms.ListView>，將 <xref:System.Windows.Forms.ListView.View%2A> 屬性設定為 <xref:System.Windows.Forms.View> 或 <xref:System.Windows.Forms.View>，然後把項目填入 <xref:System.Windows.Forms.ListView>。  
  
2.  請呼叫 <xref:System.Windows.Forms.ListView.FindItemWithText%2A> 方法，傳遞您想尋找的項目文字。  
  
3.  下列程式碼範例示範如何建立基本 <xref:System.Windows.Forms.ListView>、把項目填入其中，以及使用使用者的文字輸入來尋找清單上的項目。  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### 若要使用 X 軸和 Y 軸座標尋找項目  
  
1.  建立 <xref:System.Windows.Forms.ListView>，將 <xref:System.Windows.Forms.View> 屬性設定為 <xref:System.Windows.Forms.View> 或，<xref:System.Windows.Forms.View>，然後把項目填入 <xref:System.Windows.Forms.ListView>。  
  
2.  呼叫 <xref:System.Windows.Forms.ListView.FindNearestItem%2A> 方法，傳遞需要的 X 軸和 Y 軸座標以及您想要搜尋的方向。  
  
3.  下列程式碼範例示範如何建立基本的 <xref:System.Windows.Forms.ListView> 圖示、把項目填入其中，並擷取 <xref:System.Windows.Forms.Control.MouseDown> 事件，往上尋找最接近的項目。  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## 請參閱  
 <xref:System.Windows.Forms.ListView>   
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>   
 <xref:System.Windows.Forms.ListView.FindNearestItem%2A>   
 [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [如何：使用 Windows Form ListView 控制項加入和移除項目](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)