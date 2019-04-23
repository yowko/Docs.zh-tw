---
title: OLE DB 結構描述集合
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 6dc187b0a876d9e167a74f2381db156dde2764fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164680"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="963fc-102">OLE DB 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="963fc-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="963fc-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 OLE DB 提供者的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="963fc-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="963fc-104">Microsoft SQL Server OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="963fc-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="963fc-105">Microsoft SQL Server OLE DB 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="963fc-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="963fc-106">資料表</span><span class="sxs-lookup"><span data-stu-id="963fc-106">Tables</span></span>  
  
-   <span data-ttu-id="963fc-107">資料行</span><span class="sxs-lookup"><span data-stu-id="963fc-107">Columns</span></span>  
  
-   <span data-ttu-id="963fc-108">程序</span><span class="sxs-lookup"><span data-stu-id="963fc-108">Procedures</span></span>  
  
-   <span data-ttu-id="963fc-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="963fc-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="963fc-110">Catalog</span><span class="sxs-lookup"><span data-stu-id="963fc-110">Catalog</span></span>  
  
-   <span data-ttu-id="963fc-111">索引</span><span class="sxs-lookup"><span data-stu-id="963fc-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="963fc-112">資料表</span><span class="sxs-lookup"><span data-stu-id="963fc-112">Tables</span></span>  
  
|<span data-ttu-id="963fc-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-113">ColumnName</span></span>|<span data-ttu-id="963fc-114">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-115">TABLE_CATALOG</span></span>|<span data-ttu-id="963fc-116">String</span><span class="sxs-lookup"><span data-stu-id="963fc-116">String</span></span>|  
|<span data-ttu-id="963fc-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="963fc-118">String</span><span class="sxs-lookup"><span data-stu-id="963fc-118">String</span></span>|  
|<span data-ttu-id="963fc-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-119">TABLE_NAME</span></span>|<span data-ttu-id="963fc-120">String</span><span class="sxs-lookup"><span data-stu-id="963fc-120">String</span></span>|  
|<span data-ttu-id="963fc-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="963fc-121">TABLE_TYPE</span></span>|<span data-ttu-id="963fc-122">String</span><span class="sxs-lookup"><span data-stu-id="963fc-122">String</span></span>|  
|<span data-ttu-id="963fc-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="963fc-123">TABLE_GUID</span></span>|<span data-ttu-id="963fc-124">Guid</span><span class="sxs-lookup"><span data-stu-id="963fc-124">Guid</span></span>|  
|<span data-ttu-id="963fc-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="963fc-125">DESCRIPTION</span></span>|<span data-ttu-id="963fc-126">String</span><span class="sxs-lookup"><span data-stu-id="963fc-126">String</span></span>|  
|<span data-ttu-id="963fc-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="963fc-127">TABLE_PROPID</span></span>|<span data-ttu-id="963fc-128">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-128">Int64</span></span>|  
|<span data-ttu-id="963fc-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="963fc-129">DATE_CREATED</span></span>|<span data-ttu-id="963fc-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="963fc-130">DateTime</span></span>|  
|<span data-ttu-id="963fc-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="963fc-131">DATE_MODIFIED</span></span>|<span data-ttu-id="963fc-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="963fc-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="963fc-133">資料行</span><span class="sxs-lookup"><span data-stu-id="963fc-133">Columns</span></span>  
  
|<span data-ttu-id="963fc-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-134">ColumnName</span></span>|<span data-ttu-id="963fc-135">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-136">TABLE_CATALOG</span></span>|<span data-ttu-id="963fc-137">String</span><span class="sxs-lookup"><span data-stu-id="963fc-137">String</span></span>|  
|<span data-ttu-id="963fc-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="963fc-139">String</span><span class="sxs-lookup"><span data-stu-id="963fc-139">String</span></span>|  
|<span data-ttu-id="963fc-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-140">TABLE_NAME</span></span>|<span data-ttu-id="963fc-141">String</span><span class="sxs-lookup"><span data-stu-id="963fc-141">String</span></span>|  
|<span data-ttu-id="963fc-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-142">COLUMN_NAME</span></span>|<span data-ttu-id="963fc-143">String</span><span class="sxs-lookup"><span data-stu-id="963fc-143">String</span></span>|  
|<span data-ttu-id="963fc-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="963fc-144">COLUMN_GUID</span></span>|<span data-ttu-id="963fc-145">Guid</span><span class="sxs-lookup"><span data-stu-id="963fc-145">Guid</span></span>|  
|<span data-ttu-id="963fc-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="963fc-146">COLUMN_PROPID</span></span>|<span data-ttu-id="963fc-147">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-147">Int64</span></span>|  
|<span data-ttu-id="963fc-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="963fc-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="963fc-149">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-149">Int64</span></span>|  
|<span data-ttu-id="963fc-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="963fc-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="963fc-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-151">Boolean</span></span>|  
|<span data-ttu-id="963fc-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="963fc-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="963fc-153">String</span><span class="sxs-lookup"><span data-stu-id="963fc-153">String</span></span>|  
|<span data-ttu-id="963fc-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="963fc-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="963fc-155">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-155">Int64</span></span>|  
|<span data-ttu-id="963fc-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="963fc-156">IS_NULLABLE</span></span>|<span data-ttu-id="963fc-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-157">Boolean</span></span>|  
|<span data-ttu-id="963fc-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="963fc-158">DATA_TYPE</span></span>|<span data-ttu-id="963fc-159">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-159">Int32</span></span>|  
|<span data-ttu-id="963fc-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="963fc-160">TYPE_GUID</span></span>|<span data-ttu-id="963fc-161">Guid</span><span class="sxs-lookup"><span data-stu-id="963fc-161">Guid</span></span>|  
|<span data-ttu-id="963fc-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="963fc-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="963fc-163">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-163">Int64</span></span>|  
|<span data-ttu-id="963fc-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="963fc-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="963fc-165">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-165">Int64</span></span>|  
|<span data-ttu-id="963fc-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="963fc-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="963fc-167">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-167">Int32</span></span>|  
|<span data-ttu-id="963fc-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="963fc-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="963fc-169">Int16</span><span class="sxs-lookup"><span data-stu-id="963fc-169">Int16</span></span>|  
|<span data-ttu-id="963fc-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="963fc-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="963fc-171">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-171">Int64</span></span>|  
|<span data-ttu-id="963fc-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="963fc-173">String</span><span class="sxs-lookup"><span data-stu-id="963fc-173">String</span></span>|  
|<span data-ttu-id="963fc-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="963fc-175">String</span><span class="sxs-lookup"><span data-stu-id="963fc-175">String</span></span>|  
|<span data-ttu-id="963fc-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="963fc-177">String</span><span class="sxs-lookup"><span data-stu-id="963fc-177">String</span></span>|  
|<span data-ttu-id="963fc-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="963fc-179">String</span><span class="sxs-lookup"><span data-stu-id="963fc-179">String</span></span>|  
|<span data-ttu-id="963fc-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="963fc-181">String</span><span class="sxs-lookup"><span data-stu-id="963fc-181">String</span></span>|  
|<span data-ttu-id="963fc-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-182">COLLATION_NAME</span></span>|<span data-ttu-id="963fc-183">String</span><span class="sxs-lookup"><span data-stu-id="963fc-183">String</span></span>|  
|<span data-ttu-id="963fc-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="963fc-185">String</span><span class="sxs-lookup"><span data-stu-id="963fc-185">String</span></span>|  
|<span data-ttu-id="963fc-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="963fc-187">String</span><span class="sxs-lookup"><span data-stu-id="963fc-187">String</span></span>|  
|<span data-ttu-id="963fc-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-188">DOMAIN_NAME</span></span>|<span data-ttu-id="963fc-189">String</span><span class="sxs-lookup"><span data-stu-id="963fc-189">String</span></span>|  
|<span data-ttu-id="963fc-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="963fc-190">DESCRIPTION</span></span>|<span data-ttu-id="963fc-191">String</span><span class="sxs-lookup"><span data-stu-id="963fc-191">String</span></span>|  
|<span data-ttu-id="963fc-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="963fc-192">COLUMN_LCID</span></span>|<span data-ttu-id="963fc-193">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-193">Int32</span></span>|  
|<span data-ttu-id="963fc-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="963fc-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="963fc-195">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-195">Int32</span></span>|  
|<span data-ttu-id="963fc-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="963fc-196">COLUMN_SORTID</span></span>|<span data-ttu-id="963fc-197">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-197">Int32</span></span>|  
|<span data-ttu-id="963fc-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="963fc-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="963fc-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="963fc-199">Byte[]</span></span>|  
|<span data-ttu-id="963fc-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="963fc-200">IS_COMPUTED</span></span>|<span data-ttu-id="963fc-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="963fc-202">程序</span><span class="sxs-lookup"><span data-stu-id="963fc-202">Procedures</span></span>  
  
|<span data-ttu-id="963fc-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-203">ColumnName</span></span>|<span data-ttu-id="963fc-204">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="963fc-206">String</span><span class="sxs-lookup"><span data-stu-id="963fc-206">String</span></span>|  
|<span data-ttu-id="963fc-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="963fc-208">String</span><span class="sxs-lookup"><span data-stu-id="963fc-208">String</span></span>|  
|<span data-ttu-id="963fc-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="963fc-210">String</span><span class="sxs-lookup"><span data-stu-id="963fc-210">String</span></span>|  
|<span data-ttu-id="963fc-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="963fc-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="963fc-212">Int16</span><span class="sxs-lookup"><span data-stu-id="963fc-212">Int16</span></span>|  
|<span data-ttu-id="963fc-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="963fc-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="963fc-214">String</span><span class="sxs-lookup"><span data-stu-id="963fc-214">String</span></span>|  
|<span data-ttu-id="963fc-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="963fc-215">DESCRIPTION</span></span>|<span data-ttu-id="963fc-216">String</span><span class="sxs-lookup"><span data-stu-id="963fc-216">String</span></span>|  
|<span data-ttu-id="963fc-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="963fc-217">DATE_CREATED</span></span>|<span data-ttu-id="963fc-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="963fc-218">DateTime</span></span>|  
|<span data-ttu-id="963fc-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="963fc-219">DATE_MODIFIED</span></span>|<span data-ttu-id="963fc-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="963fc-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="963fc-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="963fc-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="963fc-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-222">ColumnName</span></span>|<span data-ttu-id="963fc-223">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="963fc-225">String</span><span class="sxs-lookup"><span data-stu-id="963fc-225">String</span></span>|  
|<span data-ttu-id="963fc-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="963fc-227">String</span><span class="sxs-lookup"><span data-stu-id="963fc-227">String</span></span>|  
|<span data-ttu-id="963fc-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="963fc-229">String</span><span class="sxs-lookup"><span data-stu-id="963fc-229">String</span></span>|  
|<span data-ttu-id="963fc-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-230">PARAMETER_NAME</span></span>|<span data-ttu-id="963fc-231">String</span><span class="sxs-lookup"><span data-stu-id="963fc-231">String</span></span>|  
|<span data-ttu-id="963fc-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="963fc-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="963fc-233">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-233">Int32</span></span>|  
|<span data-ttu-id="963fc-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="963fc-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="963fc-235">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-235">Int32</span></span>|  
|<span data-ttu-id="963fc-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="963fc-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="963fc-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-237">Boolean</span></span>|  
|<span data-ttu-id="963fc-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="963fc-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="963fc-239">String</span><span class="sxs-lookup"><span data-stu-id="963fc-239">String</span></span>|  
|<span data-ttu-id="963fc-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="963fc-240">IS_NULLABLE</span></span>|<span data-ttu-id="963fc-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-241">Boolean</span></span>|  
|<span data-ttu-id="963fc-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="963fc-242">DATA_TYPE</span></span>|<span data-ttu-id="963fc-243">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-243">Int32</span></span>|  
|<span data-ttu-id="963fc-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="963fc-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="963fc-245">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-245">Int64</span></span>|  
|<span data-ttu-id="963fc-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="963fc-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="963fc-247">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-247">Int64</span></span>|  
|<span data-ttu-id="963fc-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="963fc-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="963fc-249">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-249">Int32</span></span>|  
|<span data-ttu-id="963fc-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="963fc-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="963fc-251">Int16</span><span class="sxs-lookup"><span data-stu-id="963fc-251">Int16</span></span>|  
|<span data-ttu-id="963fc-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="963fc-252">DESCRIPTION</span></span>|<span data-ttu-id="963fc-253">String</span><span class="sxs-lookup"><span data-stu-id="963fc-253">String</span></span>|  
|<span data-ttu-id="963fc-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-254">TYPE_NAME</span></span>|<span data-ttu-id="963fc-255">String</span><span class="sxs-lookup"><span data-stu-id="963fc-255">String</span></span>|  
|<span data-ttu-id="963fc-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="963fc-257">String</span><span class="sxs-lookup"><span data-stu-id="963fc-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="963fc-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="963fc-258">Catalog</span></span>  
  
|<span data-ttu-id="963fc-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-259">ColumnName</span></span>|<span data-ttu-id="963fc-260">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-261">CATALOG_NAME</span></span>|<span data-ttu-id="963fc-262">String</span><span class="sxs-lookup"><span data-stu-id="963fc-262">String</span></span>|  
|<span data-ttu-id="963fc-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="963fc-263">DESCRIPTION</span></span>|<span data-ttu-id="963fc-264">String</span><span class="sxs-lookup"><span data-stu-id="963fc-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="963fc-265">索引</span><span class="sxs-lookup"><span data-stu-id="963fc-265">Indexes</span></span>  
  
|<span data-ttu-id="963fc-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-266">ColumnName</span></span>|<span data-ttu-id="963fc-267">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-268">TABLE_CATALOG</span></span>|<span data-ttu-id="963fc-269">String</span><span class="sxs-lookup"><span data-stu-id="963fc-269">String</span></span>|  
|<span data-ttu-id="963fc-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="963fc-271">String</span><span class="sxs-lookup"><span data-stu-id="963fc-271">String</span></span>|  
|<span data-ttu-id="963fc-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-272">TABLE_NAME</span></span>|<span data-ttu-id="963fc-273">String</span><span class="sxs-lookup"><span data-stu-id="963fc-273">String</span></span>|  
|<span data-ttu-id="963fc-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-274">INDEX_CATALOG</span></span>|<span data-ttu-id="963fc-275">String</span><span class="sxs-lookup"><span data-stu-id="963fc-275">String</span></span>|  
|<span data-ttu-id="963fc-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="963fc-277">String</span><span class="sxs-lookup"><span data-stu-id="963fc-277">String</span></span>|  
|<span data-ttu-id="963fc-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-278">INDEX_NAME</span></span>|<span data-ttu-id="963fc-279">String</span><span class="sxs-lookup"><span data-stu-id="963fc-279">String</span></span>|  
|<span data-ttu-id="963fc-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="963fc-280">PRIMARY_KEY</span></span>|<span data-ttu-id="963fc-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-281">Boolean</span></span>|  
|<span data-ttu-id="963fc-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="963fc-282">UNIQUE</span></span>|<span data-ttu-id="963fc-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-283">Boolean</span></span>|  
|<span data-ttu-id="963fc-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="963fc-284">CLUSTERED</span></span>|<span data-ttu-id="963fc-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-285">Boolean</span></span>|  
|<span data-ttu-id="963fc-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="963fc-286">TYPE</span></span>|<span data-ttu-id="963fc-287">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-287">Int32</span></span>|  
|<span data-ttu-id="963fc-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="963fc-288">FILL_FACTOR</span></span>|<span data-ttu-id="963fc-289">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-289">Int32</span></span>|  
|<span data-ttu-id="963fc-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="963fc-290">INITIAL_SIZE</span></span>|<span data-ttu-id="963fc-291">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-291">Int32</span></span>|  
|<span data-ttu-id="963fc-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="963fc-292">NULLS</span></span>|<span data-ttu-id="963fc-293">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-293">Int32</span></span>|  
|<span data-ttu-id="963fc-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="963fc-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="963fc-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-295">Boolean</span></span>|  
|<span data-ttu-id="963fc-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="963fc-296">AUTO_UPDATE</span></span>|<span data-ttu-id="963fc-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-297">Boolean</span></span>|  
|<span data-ttu-id="963fc-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="963fc-298">NULL_COLLATION</span></span>|<span data-ttu-id="963fc-299">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-299">Int32</span></span>|  
|<span data-ttu-id="963fc-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="963fc-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="963fc-301">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-301">Int64</span></span>|  
|<span data-ttu-id="963fc-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-302">COLUMN_NAME</span></span>|<span data-ttu-id="963fc-303">String</span><span class="sxs-lookup"><span data-stu-id="963fc-303">String</span></span>|  
|<span data-ttu-id="963fc-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="963fc-304">COLUMN_GUID</span></span>|<span data-ttu-id="963fc-305">Guid</span><span class="sxs-lookup"><span data-stu-id="963fc-305">Guid</span></span>|  
|<span data-ttu-id="963fc-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="963fc-306">COLUMN_PROPID</span></span>|<span data-ttu-id="963fc-307">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-307">Int64</span></span>|  
|<span data-ttu-id="963fc-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="963fc-308">COLLATION</span></span>|<span data-ttu-id="963fc-309">Int16</span><span class="sxs-lookup"><span data-stu-id="963fc-309">Int16</span></span>|  
|<span data-ttu-id="963fc-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="963fc-310">CARDINALITY</span></span>|<span data-ttu-id="963fc-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="963fc-311">Decimal</span></span>|  
|<span data-ttu-id="963fc-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="963fc-312">PAGES</span></span>|<span data-ttu-id="963fc-313">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-313">Int32</span></span>|  
|<span data-ttu-id="963fc-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="963fc-314">FILTER_CONDITION</span></span>|<span data-ttu-id="963fc-315">String</span><span class="sxs-lookup"><span data-stu-id="963fc-315">String</span></span>|  
|<span data-ttu-id="963fc-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="963fc-316">INTEGRATED</span></span>|<span data-ttu-id="963fc-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="963fc-318">Microsoft Oracle OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="963fc-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="963fc-319">除了通用結構描述集合之外，Microsoft Oracle OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="963fc-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="963fc-320">資料表</span><span class="sxs-lookup"><span data-stu-id="963fc-320">Tables</span></span>  
  
-   <span data-ttu-id="963fc-321">資料行</span><span class="sxs-lookup"><span data-stu-id="963fc-321">Columns</span></span>  
  
-   <span data-ttu-id="963fc-322">程序</span><span class="sxs-lookup"><span data-stu-id="963fc-322">Procedures</span></span>  
  
-   <span data-ttu-id="963fc-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="963fc-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="963fc-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="963fc-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="963fc-325">檢視</span><span class="sxs-lookup"><span data-stu-id="963fc-325">Views</span></span>  
  
-   <span data-ttu-id="963fc-326">索引</span><span class="sxs-lookup"><span data-stu-id="963fc-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="963fc-327">資料表</span><span class="sxs-lookup"><span data-stu-id="963fc-327">Tables</span></span>  
  
|<span data-ttu-id="963fc-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-328">ColumnName</span></span>|<span data-ttu-id="963fc-329">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-330">TABLE_CATALOG</span></span>|<span data-ttu-id="963fc-331">String</span><span class="sxs-lookup"><span data-stu-id="963fc-331">String</span></span>|  
|<span data-ttu-id="963fc-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="963fc-333">String</span><span class="sxs-lookup"><span data-stu-id="963fc-333">String</span></span>|  
|<span data-ttu-id="963fc-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-334">TABLE_NAME</span></span>|<span data-ttu-id="963fc-335">String</span><span class="sxs-lookup"><span data-stu-id="963fc-335">String</span></span>|  
|<span data-ttu-id="963fc-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="963fc-336">TABLE_TYPE</span></span>|<span data-ttu-id="963fc-337">String</span><span class="sxs-lookup"><span data-stu-id="963fc-337">String</span></span>|  
|<span data-ttu-id="963fc-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="963fc-338">TABLE_GUID</span></span>|<span data-ttu-id="963fc-339">Guid</span><span class="sxs-lookup"><span data-stu-id="963fc-339">Guid</span></span>|  
|<span data-ttu-id="963fc-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="963fc-340">DESCRIPTION</span></span>|<span data-ttu-id="963fc-341">String</span><span class="sxs-lookup"><span data-stu-id="963fc-341">String</span></span>|  
|<span data-ttu-id="963fc-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="963fc-342">TABLE_PROPID</span></span>|<span data-ttu-id="963fc-343">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-343">Int64</span></span>|  
|<span data-ttu-id="963fc-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="963fc-344">DATE_CREATED</span></span>|<span data-ttu-id="963fc-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="963fc-345">DateTime</span></span>|  
|<span data-ttu-id="963fc-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="963fc-346">DATE_MODIFIED</span></span>|<span data-ttu-id="963fc-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="963fc-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="963fc-348">資料行</span><span class="sxs-lookup"><span data-stu-id="963fc-348">Columns</span></span>  
  
|<span data-ttu-id="963fc-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-349">ColumnName</span></span>|<span data-ttu-id="963fc-350">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-351">TABLE_CATALOG</span></span>|<span data-ttu-id="963fc-352">String</span><span class="sxs-lookup"><span data-stu-id="963fc-352">String</span></span>|  
|<span data-ttu-id="963fc-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="963fc-354">String</span><span class="sxs-lookup"><span data-stu-id="963fc-354">String</span></span>|  
|<span data-ttu-id="963fc-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-355">TABLE_NAME</span></span>|<span data-ttu-id="963fc-356">String</span><span class="sxs-lookup"><span data-stu-id="963fc-356">String</span></span>|  
|<span data-ttu-id="963fc-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-357">COLUMN_NAME</span></span>|<span data-ttu-id="963fc-358">String</span><span class="sxs-lookup"><span data-stu-id="963fc-358">String</span></span>|  
|<span data-ttu-id="963fc-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="963fc-359">COLUMN_GUID</span></span>|<span data-ttu-id="963fc-360">Guid</span><span class="sxs-lookup"><span data-stu-id="963fc-360">Guid</span></span>|  
|<span data-ttu-id="963fc-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="963fc-361">COLUMN_PROPID</span></span>|<span data-ttu-id="963fc-362">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-362">Int64</span></span>|  
|<span data-ttu-id="963fc-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="963fc-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="963fc-364">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-364">Int64</span></span>|  
|<span data-ttu-id="963fc-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="963fc-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="963fc-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-366">Boolean</span></span>|  
|<span data-ttu-id="963fc-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="963fc-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="963fc-368">String</span><span class="sxs-lookup"><span data-stu-id="963fc-368">String</span></span>|  
|<span data-ttu-id="963fc-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="963fc-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="963fc-370">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-370">Int64</span></span>|  
|<span data-ttu-id="963fc-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="963fc-371">IS_NULLABLE</span></span>|<span data-ttu-id="963fc-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-372">Boolean</span></span>|  
|<span data-ttu-id="963fc-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="963fc-373">DATA_TYPE</span></span>|<span data-ttu-id="963fc-374">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-374">Int32</span></span>|  
|<span data-ttu-id="963fc-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="963fc-375">TYPE_GUID</span></span>|<span data-ttu-id="963fc-376">Guid</span><span class="sxs-lookup"><span data-stu-id="963fc-376">Guid</span></span>|  
|<span data-ttu-id="963fc-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="963fc-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="963fc-378">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-378">Int64</span></span>|  
|<span data-ttu-id="963fc-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="963fc-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="963fc-380">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-380">Int64</span></span>|  
|<span data-ttu-id="963fc-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="963fc-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="963fc-382">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-382">Int32</span></span>|  
|<span data-ttu-id="963fc-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="963fc-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="963fc-384">Int16</span><span class="sxs-lookup"><span data-stu-id="963fc-384">Int16</span></span>|  
|<span data-ttu-id="963fc-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="963fc-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="963fc-386">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-386">Int64</span></span>|  
|<span data-ttu-id="963fc-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="963fc-388">String</span><span class="sxs-lookup"><span data-stu-id="963fc-388">String</span></span>|  
|<span data-ttu-id="963fc-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="963fc-390">String</span><span class="sxs-lookup"><span data-stu-id="963fc-390">String</span></span>|  
|<span data-ttu-id="963fc-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="963fc-392">String</span><span class="sxs-lookup"><span data-stu-id="963fc-392">String</span></span>|  
|<span data-ttu-id="963fc-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="963fc-394">String</span><span class="sxs-lookup"><span data-stu-id="963fc-394">String</span></span>|  
|<span data-ttu-id="963fc-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="963fc-396">String</span><span class="sxs-lookup"><span data-stu-id="963fc-396">String</span></span>|  
|<span data-ttu-id="963fc-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-397">COLLATION_NAME</span></span>|<span data-ttu-id="963fc-398">String</span><span class="sxs-lookup"><span data-stu-id="963fc-398">String</span></span>|  
|<span data-ttu-id="963fc-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="963fc-400">String</span><span class="sxs-lookup"><span data-stu-id="963fc-400">String</span></span>|  
|<span data-ttu-id="963fc-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="963fc-402">String</span><span class="sxs-lookup"><span data-stu-id="963fc-402">String</span></span>|  
|<span data-ttu-id="963fc-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-403">DOMAIN_NAME</span></span>|<span data-ttu-id="963fc-404">String</span><span class="sxs-lookup"><span data-stu-id="963fc-404">String</span></span>|  
|<span data-ttu-id="963fc-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="963fc-405">DESCRIPTION</span></span>|<span data-ttu-id="963fc-406">String</span><span class="sxs-lookup"><span data-stu-id="963fc-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="963fc-407">程序</span><span class="sxs-lookup"><span data-stu-id="963fc-407">Procedures</span></span>  
  
|<span data-ttu-id="963fc-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-408">ColumnName</span></span>|<span data-ttu-id="963fc-409">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="963fc-411">String</span><span class="sxs-lookup"><span data-stu-id="963fc-411">String</span></span>|  
|<span data-ttu-id="963fc-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="963fc-413">String</span><span class="sxs-lookup"><span data-stu-id="963fc-413">String</span></span>|  
|<span data-ttu-id="963fc-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="963fc-415">String</span><span class="sxs-lookup"><span data-stu-id="963fc-415">String</span></span>|  
|<span data-ttu-id="963fc-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="963fc-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="963fc-417">Int16</span><span class="sxs-lookup"><span data-stu-id="963fc-417">Int16</span></span>|  
|<span data-ttu-id="963fc-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="963fc-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="963fc-419">String</span><span class="sxs-lookup"><span data-stu-id="963fc-419">String</span></span>|  
|<span data-ttu-id="963fc-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="963fc-420">DESCRIPTION</span></span>|<span data-ttu-id="963fc-421">String</span><span class="sxs-lookup"><span data-stu-id="963fc-421">String</span></span>|  
|<span data-ttu-id="963fc-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="963fc-422">DATE_CREATED</span></span>|<span data-ttu-id="963fc-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="963fc-423">DateTime</span></span>|  
|<span data-ttu-id="963fc-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="963fc-424">DATE_MODIFIED</span></span>|<span data-ttu-id="963fc-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="963fc-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="963fc-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="963fc-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="963fc-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-427">ColumnName</span></span>|<span data-ttu-id="963fc-428">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="963fc-430">String</span><span class="sxs-lookup"><span data-stu-id="963fc-430">String</span></span>|  
|<span data-ttu-id="963fc-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="963fc-432">String</span><span class="sxs-lookup"><span data-stu-id="963fc-432">String</span></span>|  
|<span data-ttu-id="963fc-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="963fc-434">String</span><span class="sxs-lookup"><span data-stu-id="963fc-434">String</span></span>|  
|<span data-ttu-id="963fc-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-435">COLUMN_NAME</span></span>|<span data-ttu-id="963fc-436">String</span><span class="sxs-lookup"><span data-stu-id="963fc-436">String</span></span>|  
|<span data-ttu-id="963fc-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="963fc-437">COLUMN_GUID</span></span>|<span data-ttu-id="963fc-438">Guid</span><span class="sxs-lookup"><span data-stu-id="963fc-438">Guid</span></span>|  
|<span data-ttu-id="963fc-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="963fc-439">COLUMN_PROPID</span></span>|<span data-ttu-id="963fc-440">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-440">Int64</span></span>|  
|<span data-ttu-id="963fc-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="963fc-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="963fc-442">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-442">Int64</span></span>|  
|<span data-ttu-id="963fc-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="963fc-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="963fc-444">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-444">Int64</span></span>|  
|<span data-ttu-id="963fc-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="963fc-445">IS_NULLABLE</span></span>|<span data-ttu-id="963fc-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-446">Boolean</span></span>|  
|<span data-ttu-id="963fc-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="963fc-447">DATA_TYPE</span></span>|<span data-ttu-id="963fc-448">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-448">Int32</span></span>|  
|<span data-ttu-id="963fc-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="963fc-449">TYPE_GUID</span></span>|<span data-ttu-id="963fc-450">Guid</span><span class="sxs-lookup"><span data-stu-id="963fc-450">Guid</span></span>|  
|<span data-ttu-id="963fc-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="963fc-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="963fc-452">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-452">Int64</span></span>|  
|<span data-ttu-id="963fc-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="963fc-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="963fc-454">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-454">Int64</span></span>|  
|<span data-ttu-id="963fc-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="963fc-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="963fc-456">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-456">Int32</span></span>|  
|<span data-ttu-id="963fc-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="963fc-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="963fc-458">Int16</span><span class="sxs-lookup"><span data-stu-id="963fc-458">Int16</span></span>|  
|<span data-ttu-id="963fc-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="963fc-459">DESCRIPTION</span></span>|<span data-ttu-id="963fc-460">String</span><span class="sxs-lookup"><span data-stu-id="963fc-460">String</span></span>|  
|<span data-ttu-id="963fc-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="963fc-461">OVERLOAD</span></span>|<span data-ttu-id="963fc-462">Int16</span><span class="sxs-lookup"><span data-stu-id="963fc-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="963fc-463">檢視</span><span class="sxs-lookup"><span data-stu-id="963fc-463">Views</span></span>  
  
|<span data-ttu-id="963fc-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-464">ColumnName</span></span>|<span data-ttu-id="963fc-465">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-466">TABLE_CATALOG</span></span>|<span data-ttu-id="963fc-467">String</span><span class="sxs-lookup"><span data-stu-id="963fc-467">String</span></span>|  
|<span data-ttu-id="963fc-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="963fc-469">String</span><span class="sxs-lookup"><span data-stu-id="963fc-469">String</span></span>|  
|<span data-ttu-id="963fc-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-470">TABLE_NAME</span></span>|<span data-ttu-id="963fc-471">String</span><span class="sxs-lookup"><span data-stu-id="963fc-471">String</span></span>|  
|<span data-ttu-id="963fc-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="963fc-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="963fc-473">String</span><span class="sxs-lookup"><span data-stu-id="963fc-473">String</span></span>|  
|<span data-ttu-id="963fc-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="963fc-474">CHECK_OPTION</span></span>|<span data-ttu-id="963fc-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-475">Boolean</span></span>|  
|<span data-ttu-id="963fc-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="963fc-476">IS_UPDATABLE</span></span>|<span data-ttu-id="963fc-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-477">Boolean</span></span>|  
|<span data-ttu-id="963fc-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="963fc-478">DESCRIPTION</span></span>|<span data-ttu-id="963fc-479">String</span><span class="sxs-lookup"><span data-stu-id="963fc-479">String</span></span>|  
|<span data-ttu-id="963fc-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="963fc-480">DATE_CREATED</span></span>|<span data-ttu-id="963fc-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="963fc-481">DateTime</span></span>|  
|<span data-ttu-id="963fc-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="963fc-482">DATE_MODIFIED</span></span>|<span data-ttu-id="963fc-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="963fc-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="963fc-484">索引</span><span class="sxs-lookup"><span data-stu-id="963fc-484">Indexes</span></span>  
  
|<span data-ttu-id="963fc-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-485">ColumnName</span></span>|<span data-ttu-id="963fc-486">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-487">TABLE_CATALOG</span></span>|<span data-ttu-id="963fc-488">String</span><span class="sxs-lookup"><span data-stu-id="963fc-488">String</span></span>|  
|<span data-ttu-id="963fc-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="963fc-490">String</span><span class="sxs-lookup"><span data-stu-id="963fc-490">String</span></span>|  
|<span data-ttu-id="963fc-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-491">TABLE_NAME</span></span>|<span data-ttu-id="963fc-492">String</span><span class="sxs-lookup"><span data-stu-id="963fc-492">String</span></span>|  
|<span data-ttu-id="963fc-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-493">INDEX_CATALOG</span></span>|<span data-ttu-id="963fc-494">String</span><span class="sxs-lookup"><span data-stu-id="963fc-494">String</span></span>|  
|<span data-ttu-id="963fc-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="963fc-496">String</span><span class="sxs-lookup"><span data-stu-id="963fc-496">String</span></span>|  
|<span data-ttu-id="963fc-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-497">INDEX_NAME</span></span>|<span data-ttu-id="963fc-498">String</span><span class="sxs-lookup"><span data-stu-id="963fc-498">String</span></span>|  
|<span data-ttu-id="963fc-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="963fc-499">PRIMARY_KEY</span></span>|<span data-ttu-id="963fc-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-500">Boolean</span></span>|  
|<span data-ttu-id="963fc-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="963fc-501">UNIQUE</span></span>|<span data-ttu-id="963fc-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-502">Boolean</span></span>|  
|<span data-ttu-id="963fc-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="963fc-503">CLUSTERED</span></span>|<span data-ttu-id="963fc-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-504">Boolean</span></span>|  
|<span data-ttu-id="963fc-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="963fc-505">TYPE</span></span>|<span data-ttu-id="963fc-506">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-506">Int32</span></span>|  
|<span data-ttu-id="963fc-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="963fc-507">FILL_FACTOR</span></span>|<span data-ttu-id="963fc-508">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-508">Int32</span></span>|  
|<span data-ttu-id="963fc-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="963fc-509">INITIAL_SIZE</span></span>|<span data-ttu-id="963fc-510">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-510">Int32</span></span>|  
|<span data-ttu-id="963fc-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="963fc-511">NULLS</span></span>|<span data-ttu-id="963fc-512">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-512">Int32</span></span>|  
|<span data-ttu-id="963fc-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="963fc-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="963fc-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-514">Boolean</span></span>|  
|<span data-ttu-id="963fc-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="963fc-515">AUTO_UPDATE</span></span>|<span data-ttu-id="963fc-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-516">Boolean</span></span>|  
|<span data-ttu-id="963fc-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="963fc-517">NULL_COLLATION</span></span>|<span data-ttu-id="963fc-518">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-518">Int32</span></span>|  
|<span data-ttu-id="963fc-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="963fc-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="963fc-520">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-520">Int64</span></span>|  
|<span data-ttu-id="963fc-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-521">COLUMN_NAME</span></span>|<span data-ttu-id="963fc-522">String</span><span class="sxs-lookup"><span data-stu-id="963fc-522">String</span></span>|  
|<span data-ttu-id="963fc-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="963fc-523">COLUMN_GUID</span></span>|<span data-ttu-id="963fc-524">Guid</span><span class="sxs-lookup"><span data-stu-id="963fc-524">Guid</span></span>|  
|<span data-ttu-id="963fc-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="963fc-525">COLUMN_PROPID</span></span>|<span data-ttu-id="963fc-526">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-526">Int64</span></span>|  
|<span data-ttu-id="963fc-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="963fc-527">COLLATION</span></span>|<span data-ttu-id="963fc-528">Int16</span><span class="sxs-lookup"><span data-stu-id="963fc-528">Int16</span></span>|  
|<span data-ttu-id="963fc-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="963fc-529">CARDINALITY</span></span>|<span data-ttu-id="963fc-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="963fc-530">Decimal</span></span>|  
|<span data-ttu-id="963fc-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="963fc-531">PAGES</span></span>|<span data-ttu-id="963fc-532">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-532">Int32</span></span>|  
|<span data-ttu-id="963fc-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="963fc-533">FILTER_CONDITION</span></span>|<span data-ttu-id="963fc-534">String</span><span class="sxs-lookup"><span data-stu-id="963fc-534">String</span></span>|  
|<span data-ttu-id="963fc-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="963fc-535">INTEGRATED</span></span>|<span data-ttu-id="963fc-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="963fc-537">Microsoft Jet OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="963fc-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="963fc-538">除了通用結構描述集合之外，Microsoft Jet OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="963fc-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="963fc-539">資料表</span><span class="sxs-lookup"><span data-stu-id="963fc-539">Tables</span></span>  
  
-   <span data-ttu-id="963fc-540">資料行</span><span class="sxs-lookup"><span data-stu-id="963fc-540">Columns</span></span>  
  
-   <span data-ttu-id="963fc-541">程序</span><span class="sxs-lookup"><span data-stu-id="963fc-541">Procedures</span></span>  
  
-   <span data-ttu-id="963fc-542">檢視</span><span class="sxs-lookup"><span data-stu-id="963fc-542">Views</span></span>  
  
-   <span data-ttu-id="963fc-543">索引</span><span class="sxs-lookup"><span data-stu-id="963fc-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="963fc-544">資料表</span><span class="sxs-lookup"><span data-stu-id="963fc-544">Tables</span></span>  
  
|<span data-ttu-id="963fc-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-545">ColumnName</span></span>|<span data-ttu-id="963fc-546">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-547">TABLE_CATALOG</span></span>|<span data-ttu-id="963fc-548">String</span><span class="sxs-lookup"><span data-stu-id="963fc-548">String</span></span>|  
|<span data-ttu-id="963fc-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="963fc-550">String</span><span class="sxs-lookup"><span data-stu-id="963fc-550">String</span></span>|  
|<span data-ttu-id="963fc-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-551">TABLE_NAME</span></span>|<span data-ttu-id="963fc-552">String</span><span class="sxs-lookup"><span data-stu-id="963fc-552">String</span></span>|  
|<span data-ttu-id="963fc-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="963fc-553">TABLE_TYPE</span></span>|<span data-ttu-id="963fc-554">String</span><span class="sxs-lookup"><span data-stu-id="963fc-554">String</span></span>|  
|<span data-ttu-id="963fc-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="963fc-555">TABLE_GUID</span></span>|<span data-ttu-id="963fc-556">Guid</span><span class="sxs-lookup"><span data-stu-id="963fc-556">Guid</span></span>|  
|<span data-ttu-id="963fc-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="963fc-557">DESCRIPTION</span></span>|<span data-ttu-id="963fc-558">String</span><span class="sxs-lookup"><span data-stu-id="963fc-558">String</span></span>|  
|<span data-ttu-id="963fc-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="963fc-559">TABLE_PROPID</span></span>|<span data-ttu-id="963fc-560">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-560">Int64</span></span>|  
|<span data-ttu-id="963fc-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="963fc-561">DATE_CREATED</span></span>|<span data-ttu-id="963fc-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="963fc-562">DateTime</span></span>|  
|<span data-ttu-id="963fc-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="963fc-563">DATE_MODIFIED</span></span>|<span data-ttu-id="963fc-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="963fc-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="963fc-565">資料行</span><span class="sxs-lookup"><span data-stu-id="963fc-565">Columns</span></span>  
  
|<span data-ttu-id="963fc-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-566">ColumnName</span></span>|<span data-ttu-id="963fc-567">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-568">TABLE_CATALOG</span></span>|<span data-ttu-id="963fc-569">String</span><span class="sxs-lookup"><span data-stu-id="963fc-569">String</span></span>|  
|<span data-ttu-id="963fc-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="963fc-571">String</span><span class="sxs-lookup"><span data-stu-id="963fc-571">String</span></span>|  
|<span data-ttu-id="963fc-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-572">TABLE_NAME</span></span>|<span data-ttu-id="963fc-573">String</span><span class="sxs-lookup"><span data-stu-id="963fc-573">String</span></span>|  
|<span data-ttu-id="963fc-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-574">COLUMN_NAME</span></span>|<span data-ttu-id="963fc-575">String</span><span class="sxs-lookup"><span data-stu-id="963fc-575">String</span></span>|  
|<span data-ttu-id="963fc-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="963fc-576">COLUMN_GUID</span></span>|<span data-ttu-id="963fc-577">Guid</span><span class="sxs-lookup"><span data-stu-id="963fc-577">Guid</span></span>|  
|<span data-ttu-id="963fc-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="963fc-578">COLUMN_PROPID</span></span>|<span data-ttu-id="963fc-579">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-579">Int64</span></span>|  
|<span data-ttu-id="963fc-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="963fc-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="963fc-581">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-581">Int64</span></span>|  
|<span data-ttu-id="963fc-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="963fc-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="963fc-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-583">Boolean</span></span>|  
|<span data-ttu-id="963fc-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="963fc-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="963fc-585">String</span><span class="sxs-lookup"><span data-stu-id="963fc-585">String</span></span>|  
|<span data-ttu-id="963fc-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="963fc-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="963fc-587">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-587">Int64</span></span>|  
|<span data-ttu-id="963fc-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="963fc-588">IS_NULLABLE</span></span>|<span data-ttu-id="963fc-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-589">Boolean</span></span>|  
|<span data-ttu-id="963fc-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="963fc-590">DATA_TYPE</span></span>|<span data-ttu-id="963fc-591">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-591">Int32</span></span>|  
|<span data-ttu-id="963fc-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="963fc-592">TYPE_GUID</span></span>|<span data-ttu-id="963fc-593">Guid</span><span class="sxs-lookup"><span data-stu-id="963fc-593">Guid</span></span>|  
|<span data-ttu-id="963fc-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="963fc-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="963fc-595">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-595">Int64</span></span>|  
|<span data-ttu-id="963fc-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="963fc-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="963fc-597">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-597">Int64</span></span>|  
|<span data-ttu-id="963fc-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="963fc-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="963fc-599">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-599">Int32</span></span>|  
|<span data-ttu-id="963fc-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="963fc-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="963fc-601">Int16</span><span class="sxs-lookup"><span data-stu-id="963fc-601">Int16</span></span>|  
|<span data-ttu-id="963fc-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="963fc-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="963fc-603">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-603">Int64</span></span>|  
|<span data-ttu-id="963fc-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="963fc-605">String</span><span class="sxs-lookup"><span data-stu-id="963fc-605">String</span></span>|  
|<span data-ttu-id="963fc-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="963fc-607">String</span><span class="sxs-lookup"><span data-stu-id="963fc-607">String</span></span>|  
|<span data-ttu-id="963fc-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="963fc-609">String</span><span class="sxs-lookup"><span data-stu-id="963fc-609">String</span></span>|  
|<span data-ttu-id="963fc-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="963fc-611">String</span><span class="sxs-lookup"><span data-stu-id="963fc-611">String</span></span>|  
|<span data-ttu-id="963fc-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="963fc-613">String</span><span class="sxs-lookup"><span data-stu-id="963fc-613">String</span></span>|  
|<span data-ttu-id="963fc-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-614">COLLATION_NAME</span></span>|<span data-ttu-id="963fc-615">String</span><span class="sxs-lookup"><span data-stu-id="963fc-615">String</span></span>|  
|<span data-ttu-id="963fc-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="963fc-617">String</span><span class="sxs-lookup"><span data-stu-id="963fc-617">String</span></span>|  
|<span data-ttu-id="963fc-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="963fc-619">String</span><span class="sxs-lookup"><span data-stu-id="963fc-619">String</span></span>|  
|<span data-ttu-id="963fc-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-620">DOMAIN_NAME</span></span>|<span data-ttu-id="963fc-621">String</span><span class="sxs-lookup"><span data-stu-id="963fc-621">String</span></span>|  
|<span data-ttu-id="963fc-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="963fc-622">DESCRIPTION</span></span>|<span data-ttu-id="963fc-623">String</span><span class="sxs-lookup"><span data-stu-id="963fc-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="963fc-624">程序</span><span class="sxs-lookup"><span data-stu-id="963fc-624">Procedures</span></span>  
  
|<span data-ttu-id="963fc-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-625">ColumnName</span></span>|<span data-ttu-id="963fc-626">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="963fc-628">String</span><span class="sxs-lookup"><span data-stu-id="963fc-628">String</span></span>|  
|<span data-ttu-id="963fc-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="963fc-630">String</span><span class="sxs-lookup"><span data-stu-id="963fc-630">String</span></span>|  
|<span data-ttu-id="963fc-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="963fc-632">String</span><span class="sxs-lookup"><span data-stu-id="963fc-632">String</span></span>|  
|<span data-ttu-id="963fc-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="963fc-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="963fc-634">Int16</span><span class="sxs-lookup"><span data-stu-id="963fc-634">Int16</span></span>|  
|<span data-ttu-id="963fc-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="963fc-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="963fc-636">String</span><span class="sxs-lookup"><span data-stu-id="963fc-636">String</span></span>|  
|<span data-ttu-id="963fc-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="963fc-637">DESCRIPTION</span></span>|<span data-ttu-id="963fc-638">String</span><span class="sxs-lookup"><span data-stu-id="963fc-638">String</span></span>|  
|<span data-ttu-id="963fc-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="963fc-639">DATE_CREATED</span></span>|<span data-ttu-id="963fc-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="963fc-640">DateTime</span></span>|  
|<span data-ttu-id="963fc-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="963fc-641">DATE_MODIFIED</span></span>|<span data-ttu-id="963fc-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="963fc-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="963fc-643">檢視</span><span class="sxs-lookup"><span data-stu-id="963fc-643">Views</span></span>  
  
|<span data-ttu-id="963fc-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-644">ColumnName</span></span>|<span data-ttu-id="963fc-645">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-646">TABLE_CATALOG</span></span>|<span data-ttu-id="963fc-647">String</span><span class="sxs-lookup"><span data-stu-id="963fc-647">String</span></span>|  
|<span data-ttu-id="963fc-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="963fc-649">String</span><span class="sxs-lookup"><span data-stu-id="963fc-649">String</span></span>|  
|<span data-ttu-id="963fc-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-650">TABLE_NAME</span></span>|<span data-ttu-id="963fc-651">String</span><span class="sxs-lookup"><span data-stu-id="963fc-651">String</span></span>|  
|<span data-ttu-id="963fc-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="963fc-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="963fc-653">String</span><span class="sxs-lookup"><span data-stu-id="963fc-653">String</span></span>|  
|<span data-ttu-id="963fc-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="963fc-654">CHECK_OPTION</span></span>|<span data-ttu-id="963fc-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-655">Boolean</span></span>|  
|<span data-ttu-id="963fc-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="963fc-656">IS_UPDATABLE</span></span>|<span data-ttu-id="963fc-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-657">Boolean</span></span>|  
|<span data-ttu-id="963fc-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="963fc-658">DESCRIPTION</span></span>|<span data-ttu-id="963fc-659">String</span><span class="sxs-lookup"><span data-stu-id="963fc-659">String</span></span>|  
|<span data-ttu-id="963fc-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="963fc-660">DATE_CREATED</span></span>|<span data-ttu-id="963fc-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="963fc-661">DateTime</span></span>|  
|<span data-ttu-id="963fc-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="963fc-662">DATE_MODIFIED</span></span>|<span data-ttu-id="963fc-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="963fc-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="963fc-664">索引</span><span class="sxs-lookup"><span data-stu-id="963fc-664">Indexes</span></span>  
  
|<span data-ttu-id="963fc-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="963fc-665">ColumnName</span></span>|<span data-ttu-id="963fc-666">DataType</span><span class="sxs-lookup"><span data-stu-id="963fc-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="963fc-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-667">TABLE_CATALOG</span></span>|<span data-ttu-id="963fc-668">String</span><span class="sxs-lookup"><span data-stu-id="963fc-668">String</span></span>|  
|<span data-ttu-id="963fc-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="963fc-670">String</span><span class="sxs-lookup"><span data-stu-id="963fc-670">String</span></span>|  
|<span data-ttu-id="963fc-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-671">TABLE_NAME</span></span>|<span data-ttu-id="963fc-672">String</span><span class="sxs-lookup"><span data-stu-id="963fc-672">String</span></span>|  
|<span data-ttu-id="963fc-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="963fc-673">INDEX_CATALOG</span></span>|<span data-ttu-id="963fc-674">String</span><span class="sxs-lookup"><span data-stu-id="963fc-674">String</span></span>|  
|<span data-ttu-id="963fc-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="963fc-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="963fc-676">String</span><span class="sxs-lookup"><span data-stu-id="963fc-676">String</span></span>|  
|<span data-ttu-id="963fc-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-677">INDEX_NAME</span></span>|<span data-ttu-id="963fc-678">String</span><span class="sxs-lookup"><span data-stu-id="963fc-678">String</span></span>|  
|<span data-ttu-id="963fc-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="963fc-679">PRIMARY_KEY</span></span>|<span data-ttu-id="963fc-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-680">Boolean</span></span>|  
|<span data-ttu-id="963fc-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="963fc-681">UNIQUE</span></span>|<span data-ttu-id="963fc-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-682">Boolean</span></span>|  
|<span data-ttu-id="963fc-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="963fc-683">CLUSTERED</span></span>|<span data-ttu-id="963fc-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-684">Boolean</span></span>|  
|<span data-ttu-id="963fc-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="963fc-685">TYPE</span></span>|<span data-ttu-id="963fc-686">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-686">Int32</span></span>|  
|<span data-ttu-id="963fc-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="963fc-687">FILL_FACTOR</span></span>|<span data-ttu-id="963fc-688">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-688">Int32</span></span>|  
|<span data-ttu-id="963fc-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="963fc-689">INITIAL_SIZE</span></span>|<span data-ttu-id="963fc-690">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-690">Int32</span></span>|  
|<span data-ttu-id="963fc-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="963fc-691">NULLS</span></span>|<span data-ttu-id="963fc-692">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-692">Int32</span></span>|  
|<span data-ttu-id="963fc-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="963fc-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="963fc-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-694">Boolean</span></span>|  
|<span data-ttu-id="963fc-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="963fc-695">AUTO_UPDATE</span></span>|<span data-ttu-id="963fc-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-696">Boolean</span></span>|  
|<span data-ttu-id="963fc-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="963fc-697">NULL_COLLATION</span></span>|<span data-ttu-id="963fc-698">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-698">Int32</span></span>|  
|<span data-ttu-id="963fc-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="963fc-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="963fc-700">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-700">Int64</span></span>|  
|<span data-ttu-id="963fc-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="963fc-701">COLUMN_NAME</span></span>|<span data-ttu-id="963fc-702">String</span><span class="sxs-lookup"><span data-stu-id="963fc-702">String</span></span>|  
|<span data-ttu-id="963fc-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="963fc-703">COLUMN_GUID</span></span>|<span data-ttu-id="963fc-704">Guid</span><span class="sxs-lookup"><span data-stu-id="963fc-704">Guid</span></span>|  
|<span data-ttu-id="963fc-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="963fc-705">COLUMN_PROPID</span></span>|<span data-ttu-id="963fc-706">Int64</span><span class="sxs-lookup"><span data-stu-id="963fc-706">Int64</span></span>|  
|<span data-ttu-id="963fc-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="963fc-707">COLLATION</span></span>|<span data-ttu-id="963fc-708">Int16</span><span class="sxs-lookup"><span data-stu-id="963fc-708">Int16</span></span>|  
|<span data-ttu-id="963fc-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="963fc-709">CARDINALITY</span></span>|<span data-ttu-id="963fc-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="963fc-710">Decimal</span></span>|  
|<span data-ttu-id="963fc-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="963fc-711">PAGES</span></span>|<span data-ttu-id="963fc-712">Int32</span><span class="sxs-lookup"><span data-stu-id="963fc-712">Int32</span></span>|  
|<span data-ttu-id="963fc-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="963fc-713">FILTER_CONDITION</span></span>|<span data-ttu-id="963fc-714">String</span><span class="sxs-lookup"><span data-stu-id="963fc-714">String</span></span>|  
|<span data-ttu-id="963fc-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="963fc-715">INTEGRATED</span></span>|<span data-ttu-id="963fc-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="963fc-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="963fc-717">另請參閱</span><span class="sxs-lookup"><span data-stu-id="963fc-717">See also</span></span>

- [<span data-ttu-id="963fc-718">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="963fc-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
