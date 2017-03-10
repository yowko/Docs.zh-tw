---
title: "使用 csc.exe 建置命令列 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "組建 [C#]"
  - "命令列 [C#]"
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
caps.latest.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 28
---
# 使用 csc.exe 建置命令列
您可以在命令提示字元中輸入 C# 編譯器的可執行檔名稱 (csc.exe)，藉此叫用該編譯器。  
  
 如果您使用 **Visual Studio 命令提示字元** ] 視窗中，為您設定所有必要的環境變數。 在 Windows 7 中，您可以存取從該視窗 **啟動** ] 功能表開啟 Microsoft Visual Studio *版本*\Visual Studio 工具] 資料夾。 在 Windows 8 中，Visual Studio 命令提示字元稱為 **vs2012 開發人員命令提示字元**, ，您可以從 [開始] 畫面搜尋來找到。  
  
 如果您使用標準 [命令提示字元] 視窗，則必須先調整路徑，才能在電腦上的任何子目錄中叫用 csc.exe。 您也必須執行 vsvars32.bat 設定適當的環境變數，以便支援命令列組建。 如需 vsvars32.bat，包括如何尋找並執行它，指示的詳細資訊，請參閱 [How to︰ 設定環境變數的 Visual Studio 命令列](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)。  
  
 如果您正在只有在電腦上 [!INCLUDE[winsdklong](../../../csharp/language-reference/compiler-options/includes/winsdklong-md.md)], ，您可以使用在 C# 編譯器 **SDK 命令提示字元**, ，您可以從開啟 **Microsoft.NET Framework SDK** 功能表選項。  
  
 您也可以使用 MSBuild 以程式設計的方式建置 C# 程式。 如需詳細資訊，請參閱 [MSBuild](/visual-studio/msbuild/msbuild1)。  
  
 Csc.exe 可執行檔通常位於 microsoft.net \framework\\*版本* Windows 目錄下的資料夾。 它的位置可能依據特定電腦的實際組態而有所不同。 如果您的電腦上安裝了多個版本的 .NET Framework，您將看到這個檔案的多個版本。 如需這類安裝的詳細資訊，請參閱 [判斷其版本的.NET Framework 安裝](http://msdn.microsoft.com/zh-tw/1a87cc6a-1c4b-4c38-b878-faa9b3beae3c)。  
  
> [!TIP]
>  當您使用 Visual Studio IDE 建置專案時，您可以顯示 **csc** 命令，並在其相關聯的編譯器選項 **輸出** 視窗。 若要顯示這項資訊，請依照下列中的指示 [如何︰ 檢視中，儲存，並設定建置記錄檔](../Topic/How%20to:%20View,%20Save,%20and%20Configure%20Build%20Log%20Files.md) 若要變更的記錄資料的詳細等級 **正常** 或 **詳細**。 重建專案之後，請搜尋 **輸出** 視窗 **csc** 來尋找 C# 編譯器的引動過程。  
  
 **本主題中**  
  
-   [命令列語法規則](#vcconcommand-linebuildinganchor1)  
  
-   [命令列範例](#vcconcommand-linebuildinganchor2)  
  
-   [C# 編譯器和 c + + 編譯器輸出之間的差異](#vcconcommand-linebuildinganchor3)  
  
##  <a name="a-namevcconcommand-linebuildinganchor1a-rules-for-command-line-syntax-for-the-c-compiler"></a><a name="vcconcommand-linebuildinganchor1"></a> 如需 C# 編譯器的命令列語法的規則  
 它可解譯作業系統命令列上指定的引數時，C# 編譯器會使用下列規則︰  
  
-   引數會以空白或定位鍵的泛空白字元 (White Space) 進行分隔。  
  
-   插入號字元 (^) 無法辨識為逸出字元或分隔符號。 字元是由作業系統中的命令列剖析處理，才能傳遞給程式中的 argv 陣列。  
  
-   雙引號 ("string") 括住的字串會解譯為單一引數，不論包含在的空白字元。 有引號的字串可以內嵌到引數中。  
  
-   雙引號前面有反斜線 (\\」) 會解譯為常值雙引號字元 （"）。  
  
-   反斜線會逐字解譯，除非後面緊接著雙引號。  
  
-   如果偶數數目的反斜線後面接著雙引號，一個反斜線會放在一對反斜線，argv 陣列中，然後將雙引號解譯為字串分隔符號。  
  
-   如果奇數數目的反斜線後面接著雙引號，一個反斜線會放在一對反斜線，argv 陣列中，然後雙引號 「 逸出 」 所剩餘的反斜線。 這會導致常值雙引號 （"） 在 argv 新增。  
  
##  <a name="a-namevcconcommand-linebuildinganchor2a-sample-command-lines-for-the-c-compiler"></a><a name="vcconcommand-linebuildinganchor2"></a> C# 編譯器的命令列範例  
  
-   會產生 File.exe File.cs 順利編譯︰  
  
    ```  
    csc File.cs   
    ```  
  
-   編譯產生 File.dll File.cs:  
  
    ```  
    csc /target:library File.cs  
    ```  
  
-   會編譯 File.cs 並建立 My.exe:  
  
    ```  
    csc /out:My.exe File.cs  
    ```  
  
-   在編譯中的所有 C# 檔案目前的目錄，以最佳化和定義 DEBUG 符號。 輸出為 File2.exe:  
  
    ```  
    csc /define:DEBUG /optimize /out:File2.exe *.cs  
    ```  
  
-   編譯所有 C# 中的檔案目前的目錄產生 File2.dll 的偵錯版本。 顯示沒有標誌，沒有出現警告︰  
  
    ```  
    csc /target:library /out:File2.dll /warn:0 /nologo /debug *.cs  
    ```  
  
-   編譯所有 C# 檔案中目前的目錄 Something.xyz (DLL):  
  
    ```  
    csc /target:library /out:Something.xyz *.cs  
    ```  
  
##  <a name="a-namevcconcommand-linebuildinganchor3a-differences-between-c-compiler-and-c-compiler-output"></a><a name="vcconcommand-linebuildinganchor3"></a> C# 編譯器和 c + + 編譯器輸出之間的差異  
 叫用 C# 編譯器時並不會建立目的檔 (.obj)，而是直接建立輸出檔。 因此，C# 編譯器不需要連結器。  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)   
 [依字母順序列出 C# 編譯器選項](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)   
 [依分類排列的 C# 編譯器選項](../../../csharp/language-reference/compiler-options/listed-by-category.md)   
 [Main （） 和命令列引數](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [命令列引數](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)   
 [如何︰ 顯示命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [如何︰ 存取命令列引數使用 foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)   
 [Main （） 傳回值](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)