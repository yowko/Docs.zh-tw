### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Marshal.SizeOf 和 Marshal.PtrToStructure 多載會中斷動態程式碼

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.5.1 中，動態繫結至方法 <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>、<xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>、<xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>、<xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> 或 <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> (例如透過 Windows PowerShell、IronPython 或 C# 動態關鍵字) 可能會造成 <code>MethodInvocationExceptions</code>，因為新增了可能對指令碼引擎模稜兩可的方法多載。|
|建議|請更新指令碼，以清楚指出應使用哪個多載。 一般而言，將方法的型別參數明確轉換成 <xref:System.Type>，即可完成此作業。 如需如何解決問題的詳細資訊和範例，請參閱[這個連結](https://support.microsoft.com/kb/2909958/)。|
|範圍|次要|
|版本|4.5.1|
|類型|執行階段|

