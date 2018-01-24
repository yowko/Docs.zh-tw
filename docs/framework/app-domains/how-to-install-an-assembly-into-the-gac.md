---
title: "如何：將組件安裝到全域組件快取"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98dd4d1e75fc37820a1b1f4eccfa48f978772687
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>如何：將組件安裝到全域組件快取
有兩種方式可以將強式名稱組件安裝到全域組件快取 (GAC) 中：  
  
> [!IMPORTANT]
>  只有強式名稱組件才能安裝至 GAC。 如需如何建立強式名稱組件的資訊，請參閱[如何：使用強式名稱簽署組件](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。  
  
-   使用 [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx)。  
  
     在 Visual Studio 2012 和 Visual Studio 2013 中可以透過建立 InstallShield Limited Edition 專案的方式達到這個目的。  
  
     建議您使用這個新增組件到全域組件快取，這是最常用的方法。 安裝程式會提供全域組件快取的組件參考計數，以及其他功能。  
  
-   使用[全域組件快取工具 (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)。  
  
     您可以使用 Gacutil.exe 將強式名稱的組件新增到全域組件快取，和檢視全域組件快取的內容。  
  
    > [!NOTE]
    >  Gacutil.exe 僅適合開發用途，不應用來安裝產品組件到全域組件快取中。  
  
> [!NOTE]
>  在舊版 .NET Framework 中，可利用 Shfusion.dll Windows Shell Extension 將組件拖曳到 [檔案總管] 中，藉此安裝組件。 從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]開始，Shfusion.dll 已過時。  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a>若要使用全域組件快取工具 (Gacutil.exe)  
  
1.  在命令提示字元中輸入下列命令：  
  
     **gacutil -i** \<組件名稱>  
  
     在這個命令中，「組件名稱」是安裝在全域組件快取的組件名稱。  
  
 下列範例安裝檔名為 `hello.dll` 的組件到全域組件快取中。  
  
```  
gacutil -i hello.dll  
```  
  
 如需詳細資訊，請參閱[全域組件快取工具 (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)。  
  
### <a name="to-use-an-installshield-limited-edition-project"></a>若要使用 InstallShield Limited Edition 專案  
  
1.  開啟方案的捷徑功能表，然後依序選擇 [新增] 和 [新專案]，以將安裝和部署套件新增至方案。  
  
2.  在 [新增專案] 對話方塊中，於 [已安裝] 資料夾中選擇 [其他專案類型]、[安裝和部署]、[InstallShield Limited Edition]，然後為您的專案命名。 (出現提示時，下載、安裝並啟動 InstallShield。)  
  
3.  使用方案總管中的 [專案助理]，或是選擇方案總管中編號步驟的子步驟，執行安裝和部署專案的一般組態。設定您的安裝程式，就像未將組件新增至 GAC 一樣。  
  
4.  若要開始將組件新增至 GAC 的程序，請選擇位於方案總管的 [指定應用程式資料] 步驟下的 [檔案]。  
  
5.  在 [目的電腦的資料夾] 窗格中，開啟 [目的電腦] 的捷徑功能表，然後選擇 [顯示預先定義的資料夾]和 [[GlobalAssemblyCache]]。  
  
6.  對於方案中包含您要在全域組件快取中安裝之組件的每個專案：  
  
    1.  在 [來源電腦的資料夾] 窗格中，選擇專案。  
  
    2.  在 [目的電腦的資料夾] 窗格中，選擇 [[GlobalAssemblyCache]]。  
  
    3.  在 [來源電腦的檔案] 窗格中，選擇 [主要輸出來自 *<project_name>*]。  
  
    4.  將步驟 c 中的檔案拖曳至 [目的電腦的檔案] 窗格中 (或使用檔案的捷徑功能表上的 [複製] 和 [貼上] 命令)。  
  
## <a name="see-also"></a>請參閱  
 [使用組件和全域組件快取](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [操作說明：從全域組件快取移除組件](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [Gacutil.exe (全域組件快取工具)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [如何：使用強式名稱簽署組件](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Windows Installer 部署](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
