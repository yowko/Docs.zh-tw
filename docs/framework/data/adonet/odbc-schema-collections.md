---
title: ODBC 結構描述集合
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: f0240e99d2420b0956d3c144f837b39e094bb78a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794724"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="5877d-102">ODBC 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="5877d-102">ODBC Schema Collections</span></span>

<span data-ttu-id="5877d-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 ODBC 驅動程式的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="5877d-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="5877d-104">Microsoft SQL Server ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="5877d-104">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="5877d-105">除了通用架構集合之外，Microsoft SQL Server ODBC 驅動程式還支援下列特定的架構集合：</span><span class="sxs-lookup"><span data-stu-id="5877d-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="5877d-106">資料表</span><span class="sxs-lookup"><span data-stu-id="5877d-106">Tables</span></span>

- <span data-ttu-id="5877d-107">索引</span><span class="sxs-lookup"><span data-stu-id="5877d-107">Indexes</span></span>

- <span data-ttu-id="5877d-108">資料行</span><span class="sxs-lookup"><span data-stu-id="5877d-108">Columns</span></span>

- <span data-ttu-id="5877d-109">程序</span><span class="sxs-lookup"><span data-stu-id="5877d-109">Procedures</span></span>

- <span data-ttu-id="5877d-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5877d-110">ProcedureColumns</span></span>

- <span data-ttu-id="5877d-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5877d-111">ProcedureParameters</span></span>

- <span data-ttu-id="5877d-112">檢視</span><span class="sxs-lookup"><span data-stu-id="5877d-112">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="5877d-113">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="5877d-113">Tables and Views</span></span>

|<span data-ttu-id="5877d-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5877d-114">ColumnName</span></span>|<span data-ttu-id="5877d-115">DataType</span><span class="sxs-lookup"><span data-stu-id="5877d-115">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5877d-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="5877d-116">TABLE_CAT</span></span>|<span data-ttu-id="5877d-117">String</span><span class="sxs-lookup"><span data-stu-id="5877d-117">String</span></span>|
|<span data-ttu-id="5877d-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="5877d-118">TABLE_SCHEM</span></span>|<span data-ttu-id="5877d-119">String</span><span class="sxs-lookup"><span data-stu-id="5877d-119">String</span></span>|
|<span data-ttu-id="5877d-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-120">TABLE_NAME</span></span>|<span data-ttu-id="5877d-121">String</span><span class="sxs-lookup"><span data-stu-id="5877d-121">String</span></span>|
|<span data-ttu-id="5877d-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-122">TABLE_TYPE</span></span>|<span data-ttu-id="5877d-123">String</span><span class="sxs-lookup"><span data-stu-id="5877d-123">String</span></span>|
|<span data-ttu-id="5877d-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="5877d-124">REMARKS</span></span>|<span data-ttu-id="5877d-125">String</span><span class="sxs-lookup"><span data-stu-id="5877d-125">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="5877d-126">索引</span><span class="sxs-lookup"><span data-stu-id="5877d-126">Indexes</span></span>

|<span data-ttu-id="5877d-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5877d-127">ColumnName</span></span>|<span data-ttu-id="5877d-128">DataType</span><span class="sxs-lookup"><span data-stu-id="5877d-128">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5877d-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="5877d-129">TABLE_CAT</span></span>|<span data-ttu-id="5877d-130">String</span><span class="sxs-lookup"><span data-stu-id="5877d-130">String</span></span>|
|<span data-ttu-id="5877d-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="5877d-131">TABLE_SCHEM</span></span>|<span data-ttu-id="5877d-132">String</span><span class="sxs-lookup"><span data-stu-id="5877d-132">String</span></span>|
|<span data-ttu-id="5877d-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-133">TABLE_NAME</span></span>|<span data-ttu-id="5877d-134">String</span><span class="sxs-lookup"><span data-stu-id="5877d-134">String</span></span>|
|<span data-ttu-id="5877d-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="5877d-135">NON_UNIQUE</span></span>|<span data-ttu-id="5877d-136">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-136">Int16</span></span>|
|<span data-ttu-id="5877d-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5877d-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="5877d-138">String</span><span class="sxs-lookup"><span data-stu-id="5877d-138">String</span></span>|
|<span data-ttu-id="5877d-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-139">INDEX_NAME</span></span>|<span data-ttu-id="5877d-140">String</span><span class="sxs-lookup"><span data-stu-id="5877d-140">String</span></span>|
|<span data-ttu-id="5877d-141">類型</span><span class="sxs-lookup"><span data-stu-id="5877d-141">TYPE</span></span>|<span data-ttu-id="5877d-142">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-142">Int16</span></span>|
|<span data-ttu-id="5877d-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5877d-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="5877d-144">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-144">Int16</span></span>|
|<span data-ttu-id="5877d-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-145">COLUMN_NAME</span></span>|<span data-ttu-id="5877d-146">String</span><span class="sxs-lookup"><span data-stu-id="5877d-146">String</span></span>|
|<span data-ttu-id="5877d-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="5877d-147">ASC_OR_DESC</span></span>|<span data-ttu-id="5877d-148">String</span><span class="sxs-lookup"><span data-stu-id="5877d-148">String</span></span>|
|<span data-ttu-id="5877d-149">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="5877d-149">CARDINALITY</span></span>|<span data-ttu-id="5877d-150">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-150">Int32</span></span>|
|<span data-ttu-id="5877d-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="5877d-151">PAGES</span></span>|<span data-ttu-id="5877d-152">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-152">Int32</span></span>|
|<span data-ttu-id="5877d-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="5877d-153">FILTER_CONDITION</span></span>|<span data-ttu-id="5877d-154">String</span><span class="sxs-lookup"><span data-stu-id="5877d-154">String</span></span>|
|<span data-ttu-id="5877d-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5877d-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="5877d-156">String</span><span class="sxs-lookup"><span data-stu-id="5877d-156">String</span></span>|
|<span data-ttu-id="5877d-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="5877d-158">Byte</span><span class="sxs-lookup"><span data-stu-id="5877d-158">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="5877d-159">資料行</span><span class="sxs-lookup"><span data-stu-id="5877d-159">Columns</span></span>

|<span data-ttu-id="5877d-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5877d-160">ColumnName</span></span>|<span data-ttu-id="5877d-161">DataType</span><span class="sxs-lookup"><span data-stu-id="5877d-161">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5877d-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="5877d-162">TABLE_CAT</span></span>|<span data-ttu-id="5877d-163">String</span><span class="sxs-lookup"><span data-stu-id="5877d-163">String</span></span>|
|<span data-ttu-id="5877d-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="5877d-164">TABLE_SCHEM</span></span>|<span data-ttu-id="5877d-165">String</span><span class="sxs-lookup"><span data-stu-id="5877d-165">String</span></span>|
|<span data-ttu-id="5877d-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-166">TABLE_NAME</span></span>|<span data-ttu-id="5877d-167">String</span><span class="sxs-lookup"><span data-stu-id="5877d-167">String</span></span>|
|<span data-ttu-id="5877d-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-168">COLUMN_NAME</span></span>|<span data-ttu-id="5877d-169">String</span><span class="sxs-lookup"><span data-stu-id="5877d-169">String</span></span>|
|<span data-ttu-id="5877d-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-170">DATA_TYPE</span></span>|<span data-ttu-id="5877d-171">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-171">Int16</span></span>|
|<span data-ttu-id="5877d-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-172">TYPE_NAME</span></span>|<span data-ttu-id="5877d-173">String</span><span class="sxs-lookup"><span data-stu-id="5877d-173">String</span></span>|
|<span data-ttu-id="5877d-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="5877d-174">COLUMN_SIZE</span></span>|<span data-ttu-id="5877d-175">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-175">Int32</span></span>|
|<span data-ttu-id="5877d-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5877d-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="5877d-177">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-177">Int32</span></span>|
|<span data-ttu-id="5877d-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="5877d-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="5877d-179">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-179">Int16</span></span>|
|<span data-ttu-id="5877d-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="5877d-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="5877d-181">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-181">Int16</span></span>|
|<span data-ttu-id="5877d-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5877d-182">NULLABLE</span></span>|<span data-ttu-id="5877d-183">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-183">Int16</span></span>|
|<span data-ttu-id="5877d-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="5877d-184">REMARKS</span></span>|<span data-ttu-id="5877d-185">String</span><span class="sxs-lookup"><span data-stu-id="5877d-185">String</span></span>|
|<span data-ttu-id="5877d-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="5877d-186">COLUMN_DEF</span></span>|<span data-ttu-id="5877d-187">String</span><span class="sxs-lookup"><span data-stu-id="5877d-187">String</span></span>|
|<span data-ttu-id="5877d-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="5877d-189">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-189">Int16</span></span>|
|<span data-ttu-id="5877d-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="5877d-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="5877d-191">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-191">Int16</span></span>|
|<span data-ttu-id="5877d-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5877d-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="5877d-193">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-193">Int32</span></span>|
|<span data-ttu-id="5877d-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5877d-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="5877d-195">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-195">Int32</span></span>|
|<span data-ttu-id="5877d-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5877d-196">IS_NULLABLE</span></span>|<span data-ttu-id="5877d-197">String</span><span class="sxs-lookup"><span data-stu-id="5877d-197">String</span></span>|
|<span data-ttu-id="5877d-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5877d-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="5877d-199">String</span><span class="sxs-lookup"><span data-stu-id="5877d-199">String</span></span>|
|<span data-ttu-id="5877d-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5877d-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="5877d-201">String</span><span class="sxs-lookup"><span data-stu-id="5877d-201">String</span></span>|
|<span data-ttu-id="5877d-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="5877d-203">Byte</span><span class="sxs-lookup"><span data-stu-id="5877d-203">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="5877d-204">程序</span><span class="sxs-lookup"><span data-stu-id="5877d-204">Procedures</span></span>

|<span data-ttu-id="5877d-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5877d-205">ColumnName</span></span>|<span data-ttu-id="5877d-206">DataType</span><span class="sxs-lookup"><span data-stu-id="5877d-206">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5877d-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="5877d-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="5877d-208">String</span><span class="sxs-lookup"><span data-stu-id="5877d-208">String</span></span>|
|<span data-ttu-id="5877d-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="5877d-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="5877d-210">String</span><span class="sxs-lookup"><span data-stu-id="5877d-210">String</span></span>|
|<span data-ttu-id="5877d-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="5877d-212">String</span><span class="sxs-lookup"><span data-stu-id="5877d-212">String</span></span>|
|<span data-ttu-id="5877d-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="5877d-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="5877d-214">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-214">Int32</span></span>|
|<span data-ttu-id="5877d-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="5877d-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="5877d-216">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-216">Int32</span></span>|
|<span data-ttu-id="5877d-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="5877d-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="5877d-218">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-218">Int32</span></span>|
|<span data-ttu-id="5877d-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="5877d-219">REMARKS</span></span>|<span data-ttu-id="5877d-220">String</span><span class="sxs-lookup"><span data-stu-id="5877d-220">String</span></span>|
|<span data-ttu-id="5877d-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="5877d-222">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-222">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="5877d-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5877d-223">ProcedureColumns</span></span>

|<span data-ttu-id="5877d-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5877d-224">ColumnName</span></span>|<span data-ttu-id="5877d-225">DataType</span><span class="sxs-lookup"><span data-stu-id="5877d-225">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5877d-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="5877d-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="5877d-227">String</span><span class="sxs-lookup"><span data-stu-id="5877d-227">String</span></span>|
|<span data-ttu-id="5877d-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="5877d-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="5877d-229">String</span><span class="sxs-lookup"><span data-stu-id="5877d-229">String</span></span>|
|<span data-ttu-id="5877d-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="5877d-231">String</span><span class="sxs-lookup"><span data-stu-id="5877d-231">String</span></span>|
|<span data-ttu-id="5877d-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-232">COLUMN_NAME</span></span>|<span data-ttu-id="5877d-233">String</span><span class="sxs-lookup"><span data-stu-id="5877d-233">String</span></span>|
|<span data-ttu-id="5877d-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-234">COLUMN_TYPE</span></span>|<span data-ttu-id="5877d-235">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-235">Int16</span></span>|
|<span data-ttu-id="5877d-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-236">DATA_TYPE</span></span>|<span data-ttu-id="5877d-237">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-237">Int16</span></span>|
|<span data-ttu-id="5877d-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-238">TYPE_NAME</span></span>|<span data-ttu-id="5877d-239">String</span><span class="sxs-lookup"><span data-stu-id="5877d-239">String</span></span>|
|<span data-ttu-id="5877d-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="5877d-240">COLUMN_SIZE</span></span>|<span data-ttu-id="5877d-241">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-241">Int32</span></span>|
|<span data-ttu-id="5877d-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5877d-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="5877d-243">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-243">Int32</span></span>|
|<span data-ttu-id="5877d-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="5877d-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="5877d-245">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-245">Int16</span></span>|
|<span data-ttu-id="5877d-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="5877d-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="5877d-247">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-247">Int16</span></span>|
|<span data-ttu-id="5877d-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5877d-248">NULLABLE</span></span>|<span data-ttu-id="5877d-249">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-249">Int16</span></span>|
|<span data-ttu-id="5877d-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="5877d-250">REMARKS</span></span>|<span data-ttu-id="5877d-251">String</span><span class="sxs-lookup"><span data-stu-id="5877d-251">String</span></span>|
|<span data-ttu-id="5877d-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="5877d-252">COLUMN_DEF</span></span>|<span data-ttu-id="5877d-253">String</span><span class="sxs-lookup"><span data-stu-id="5877d-253">String</span></span>|
|<span data-ttu-id="5877d-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="5877d-255">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-255">Int16</span></span>|
|<span data-ttu-id="5877d-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="5877d-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="5877d-257">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-257">Int16</span></span>|
|<span data-ttu-id="5877d-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5877d-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="5877d-259">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-259">Int32</span></span>|
|<span data-ttu-id="5877d-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5877d-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="5877d-261">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-261">Int32</span></span>|
|<span data-ttu-id="5877d-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5877d-262">IS_NULLABLE</span></span>|<span data-ttu-id="5877d-263">String</span><span class="sxs-lookup"><span data-stu-id="5877d-263">String</span></span>|
|<span data-ttu-id="5877d-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5877d-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="5877d-265">String</span><span class="sxs-lookup"><span data-stu-id="5877d-265">String</span></span>|
|<span data-ttu-id="5877d-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5877d-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="5877d-267">String</span><span class="sxs-lookup"><span data-stu-id="5877d-267">String</span></span>|
|<span data-ttu-id="5877d-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="5877d-269">Byte</span><span class="sxs-lookup"><span data-stu-id="5877d-269">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="5877d-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5877d-270">ProcedureParameters</span></span>

|<span data-ttu-id="5877d-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5877d-271">ColumnName</span></span>|<span data-ttu-id="5877d-272">DataType</span><span class="sxs-lookup"><span data-stu-id="5877d-272">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5877d-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="5877d-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="5877d-274">String</span><span class="sxs-lookup"><span data-stu-id="5877d-274">String</span></span>|
|<span data-ttu-id="5877d-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="5877d-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="5877d-276">String</span><span class="sxs-lookup"><span data-stu-id="5877d-276">String</span></span>|
|<span data-ttu-id="5877d-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="5877d-278">String</span><span class="sxs-lookup"><span data-stu-id="5877d-278">String</span></span>|
|<span data-ttu-id="5877d-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-279">COLUMN_NAME</span></span>|<span data-ttu-id="5877d-280">String</span><span class="sxs-lookup"><span data-stu-id="5877d-280">String</span></span>|
|<span data-ttu-id="5877d-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-281">COLUMN_TYPE</span></span>|<span data-ttu-id="5877d-282">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-282">Int16</span></span>|
|<span data-ttu-id="5877d-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-283">DATA_TYPE</span></span>|<span data-ttu-id="5877d-284">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-284">Int16</span></span>|
|<span data-ttu-id="5877d-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-285">TYPE_NAME</span></span>|<span data-ttu-id="5877d-286">String</span><span class="sxs-lookup"><span data-stu-id="5877d-286">String</span></span>|
|<span data-ttu-id="5877d-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="5877d-287">COLUMN_SIZE</span></span>|<span data-ttu-id="5877d-288">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-288">Int32</span></span>|
|<span data-ttu-id="5877d-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5877d-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="5877d-290">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-290">Int32</span></span>|
|<span data-ttu-id="5877d-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="5877d-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="5877d-292">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-292">Int16</span></span>|
|<span data-ttu-id="5877d-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="5877d-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="5877d-294">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-294">Int16</span></span>|
|<span data-ttu-id="5877d-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5877d-295">NULLABLE</span></span>|<span data-ttu-id="5877d-296">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-296">Int16</span></span>|
|<span data-ttu-id="5877d-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="5877d-297">REMARKS</span></span>|<span data-ttu-id="5877d-298">String</span><span class="sxs-lookup"><span data-stu-id="5877d-298">String</span></span>|
|<span data-ttu-id="5877d-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="5877d-299">COLUMN_DEF</span></span>|<span data-ttu-id="5877d-300">String</span><span class="sxs-lookup"><span data-stu-id="5877d-300">String</span></span>|
|<span data-ttu-id="5877d-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="5877d-302">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-302">Int16</span></span>|
|<span data-ttu-id="5877d-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="5877d-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="5877d-304">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-304">Int16</span></span>|
|<span data-ttu-id="5877d-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5877d-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="5877d-306">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-306">Int32</span></span>|
|<span data-ttu-id="5877d-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5877d-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="5877d-308">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-308">Int32</span></span>|
|<span data-ttu-id="5877d-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5877d-309">IS_NULLABLE</span></span>|<span data-ttu-id="5877d-310">String</span><span class="sxs-lookup"><span data-stu-id="5877d-310">String</span></span>|
|<span data-ttu-id="5877d-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5877d-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="5877d-312">String</span><span class="sxs-lookup"><span data-stu-id="5877d-312">String</span></span>|
|<span data-ttu-id="5877d-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5877d-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="5877d-314">String</span><span class="sxs-lookup"><span data-stu-id="5877d-314">String</span></span>|
|<span data-ttu-id="5877d-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="5877d-316">Byte</span><span class="sxs-lookup"><span data-stu-id="5877d-316">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="5877d-317">Microsoft Oracle ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="5877d-317">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="5877d-318">除了通用架構集合之外，Microsoft SQL Server Oracle ODBC 驅動程式還支援下列特定的架構集合：</span><span class="sxs-lookup"><span data-stu-id="5877d-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="5877d-319">資料表</span><span class="sxs-lookup"><span data-stu-id="5877d-319">Tables</span></span>

- <span data-ttu-id="5877d-320">資料行</span><span class="sxs-lookup"><span data-stu-id="5877d-320">Columns</span></span>

- <span data-ttu-id="5877d-321">程序</span><span class="sxs-lookup"><span data-stu-id="5877d-321">Procedures</span></span>

- <span data-ttu-id="5877d-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5877d-322">ProcedureColumns</span></span>

- <span data-ttu-id="5877d-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5877d-323">ProcedureParameters</span></span>

- <span data-ttu-id="5877d-324">檢視</span><span class="sxs-lookup"><span data-stu-id="5877d-324">Views</span></span>

- <span data-ttu-id="5877d-325">索引</span><span class="sxs-lookup"><span data-stu-id="5877d-325">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="5877d-326">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="5877d-326">Tables and Views</span></span>

|<span data-ttu-id="5877d-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5877d-327">ColumnName</span></span>|<span data-ttu-id="5877d-328">DataType</span><span class="sxs-lookup"><span data-stu-id="5877d-328">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5877d-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5877d-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="5877d-330">String</span><span class="sxs-lookup"><span data-stu-id="5877d-330">String</span></span>|
|<span data-ttu-id="5877d-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="5877d-331">TABLE_OWNER</span></span>|<span data-ttu-id="5877d-332">String</span><span class="sxs-lookup"><span data-stu-id="5877d-332">String</span></span>|
|<span data-ttu-id="5877d-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-333">TABLE_NAME</span></span>|<span data-ttu-id="5877d-334">String</span><span class="sxs-lookup"><span data-stu-id="5877d-334">String</span></span>|
|<span data-ttu-id="5877d-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-335">TABLE_TYPE</span></span>|<span data-ttu-id="5877d-336">String</span><span class="sxs-lookup"><span data-stu-id="5877d-336">String</span></span>|
|<span data-ttu-id="5877d-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="5877d-337">REMARKS</span></span>|<span data-ttu-id="5877d-338">String</span><span class="sxs-lookup"><span data-stu-id="5877d-338">String</span></span>|

### <a name="columns"></a><span data-ttu-id="5877d-339">資料行</span><span class="sxs-lookup"><span data-stu-id="5877d-339">Columns</span></span>

|<span data-ttu-id="5877d-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5877d-340">ColumnName</span></span>|<span data-ttu-id="5877d-341">DataType</span><span class="sxs-lookup"><span data-stu-id="5877d-341">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5877d-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5877d-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="5877d-343">String</span><span class="sxs-lookup"><span data-stu-id="5877d-343">String</span></span>|
|<span data-ttu-id="5877d-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="5877d-344">TABLE_OWNER</span></span>|<span data-ttu-id="5877d-345">String</span><span class="sxs-lookup"><span data-stu-id="5877d-345">String</span></span>|
|<span data-ttu-id="5877d-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-346">TABLE_NAME</span></span>|<span data-ttu-id="5877d-347">String</span><span class="sxs-lookup"><span data-stu-id="5877d-347">String</span></span>|
|<span data-ttu-id="5877d-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-348">COLUMN_NAME</span></span>|<span data-ttu-id="5877d-349">String</span><span class="sxs-lookup"><span data-stu-id="5877d-349">String</span></span>|
|<span data-ttu-id="5877d-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-350">DATA_TYPE</span></span>|<span data-ttu-id="5877d-351">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-351">Int16</span></span>|
|<span data-ttu-id="5877d-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-352">TYPE_NAME</span></span>|<span data-ttu-id="5877d-353">String</span><span class="sxs-lookup"><span data-stu-id="5877d-353">String</span></span>|
|<span data-ttu-id="5877d-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="5877d-354">PRECISION</span></span>|<span data-ttu-id="5877d-355">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-355">Int32</span></span>|
|<span data-ttu-id="5877d-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="5877d-356">LENGTH</span></span>|<span data-ttu-id="5877d-357">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-357">Int32</span></span>|
|<span data-ttu-id="5877d-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="5877d-358">SCALE</span></span>|<span data-ttu-id="5877d-359">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-359">Int16</span></span>|
|<span data-ttu-id="5877d-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="5877d-360">RADIX</span></span>|<span data-ttu-id="5877d-361">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-361">Int16</span></span>|
|<span data-ttu-id="5877d-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5877d-362">NULLABLE</span></span>|<span data-ttu-id="5877d-363">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-363">Int16</span></span>|
|<span data-ttu-id="5877d-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="5877d-364">REMARKS</span></span>|<span data-ttu-id="5877d-365">String</span><span class="sxs-lookup"><span data-stu-id="5877d-365">String</span></span>|
|<span data-ttu-id="5877d-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5877d-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="5877d-367">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-367">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="5877d-368">程序</span><span class="sxs-lookup"><span data-stu-id="5877d-368">Procedures</span></span>

|<span data-ttu-id="5877d-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5877d-369">ColumnName</span></span>|<span data-ttu-id="5877d-370">DataType</span><span class="sxs-lookup"><span data-stu-id="5877d-370">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5877d-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5877d-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="5877d-372">String</span><span class="sxs-lookup"><span data-stu-id="5877d-372">String</span></span>|
|<span data-ttu-id="5877d-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="5877d-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="5877d-374">String</span><span class="sxs-lookup"><span data-stu-id="5877d-374">String</span></span>|
|<span data-ttu-id="5877d-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="5877d-376">String</span><span class="sxs-lookup"><span data-stu-id="5877d-376">String</span></span>|
|<span data-ttu-id="5877d-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="5877d-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="5877d-378">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-378">Int16</span></span>|
|<span data-ttu-id="5877d-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="5877d-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="5877d-380">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-380">Int16</span></span>|
|<span data-ttu-id="5877d-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="5877d-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="5877d-382">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-382">Int16</span></span>|
|<span data-ttu-id="5877d-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="5877d-383">REMARKS</span></span>|<span data-ttu-id="5877d-384">String</span><span class="sxs-lookup"><span data-stu-id="5877d-384">String</span></span>|
|<span data-ttu-id="5877d-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="5877d-386">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-386">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="5877d-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5877d-387">ProcedureColumns</span></span>

|<span data-ttu-id="5877d-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5877d-388">ColumnName</span></span>|<span data-ttu-id="5877d-389">DataType</span><span class="sxs-lookup"><span data-stu-id="5877d-389">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5877d-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5877d-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="5877d-391">String</span><span class="sxs-lookup"><span data-stu-id="5877d-391">String</span></span>|
|<span data-ttu-id="5877d-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="5877d-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="5877d-393">String</span><span class="sxs-lookup"><span data-stu-id="5877d-393">String</span></span>|
|<span data-ttu-id="5877d-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="5877d-395">String</span><span class="sxs-lookup"><span data-stu-id="5877d-395">String</span></span>|
|<span data-ttu-id="5877d-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-396">COLUMN_NAME</span></span>|<span data-ttu-id="5877d-397">String</span><span class="sxs-lookup"><span data-stu-id="5877d-397">String</span></span>|
|<span data-ttu-id="5877d-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-398">COLUMN_TYPE</span></span>|<span data-ttu-id="5877d-399">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-399">Int16</span></span>|
|<span data-ttu-id="5877d-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-400">DATA_TYPE</span></span>|<span data-ttu-id="5877d-401">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-401">Int16</span></span>|
|<span data-ttu-id="5877d-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-402">TYPE_NAME</span></span>|<span data-ttu-id="5877d-403">String</span><span class="sxs-lookup"><span data-stu-id="5877d-403">String</span></span>|
|<span data-ttu-id="5877d-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="5877d-404">PRECISION</span></span>|<span data-ttu-id="5877d-405">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-405">Int32</span></span>|
|<span data-ttu-id="5877d-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="5877d-406">LENGTH</span></span>|<span data-ttu-id="5877d-407">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-407">Int32</span></span>|
|<span data-ttu-id="5877d-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="5877d-408">SCALE</span></span>|<span data-ttu-id="5877d-409">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-409">Int16</span></span>|
|<span data-ttu-id="5877d-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="5877d-410">RADIX</span></span>|<span data-ttu-id="5877d-411">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-411">Int16</span></span>|
|<span data-ttu-id="5877d-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5877d-412">NULLABLE</span></span>|<span data-ttu-id="5877d-413">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-413">Int16</span></span>|
|<span data-ttu-id="5877d-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="5877d-414">REMARKS</span></span>|<span data-ttu-id="5877d-415">String</span><span class="sxs-lookup"><span data-stu-id="5877d-415">String</span></span>|
|<span data-ttu-id="5877d-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="5877d-416">OVERLOAD</span></span>|<span data-ttu-id="5877d-417">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-417">Int32</span></span>|
|<span data-ttu-id="5877d-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5877d-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="5877d-419">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-419">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="5877d-420">Microsoft Jet ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="5877d-420">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="5877d-421">除了通用結構描述集合之外，Microsoft Jet ODBC 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="5877d-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="5877d-422">資料表</span><span class="sxs-lookup"><span data-stu-id="5877d-422">Tables</span></span>

- <span data-ttu-id="5877d-423">索引</span><span class="sxs-lookup"><span data-stu-id="5877d-423">Indexes</span></span>

- <span data-ttu-id="5877d-424">資料行</span><span class="sxs-lookup"><span data-stu-id="5877d-424">Columns</span></span>

- <span data-ttu-id="5877d-425">程序</span><span class="sxs-lookup"><span data-stu-id="5877d-425">Procedures</span></span>

- <span data-ttu-id="5877d-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5877d-426">ProcedureColumns</span></span>

- <span data-ttu-id="5877d-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5877d-427">ProcedureParameters</span></span>

- <span data-ttu-id="5877d-428">檢視</span><span class="sxs-lookup"><span data-stu-id="5877d-428">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="5877d-429">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="5877d-429">Tables and Views</span></span>

|<span data-ttu-id="5877d-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5877d-430">ColumnName</span></span>|<span data-ttu-id="5877d-431">DataType</span><span class="sxs-lookup"><span data-stu-id="5877d-431">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5877d-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5877d-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="5877d-433">String</span><span class="sxs-lookup"><span data-stu-id="5877d-433">String</span></span>|
|<span data-ttu-id="5877d-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="5877d-434">TABLE_OWNER</span></span>|<span data-ttu-id="5877d-435">String</span><span class="sxs-lookup"><span data-stu-id="5877d-435">String</span></span>|
|<span data-ttu-id="5877d-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-436">TABLE_NAME</span></span>|<span data-ttu-id="5877d-437">String</span><span class="sxs-lookup"><span data-stu-id="5877d-437">String</span></span>|
|<span data-ttu-id="5877d-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-438">TABLE_TYPE</span></span>|<span data-ttu-id="5877d-439">String</span><span class="sxs-lookup"><span data-stu-id="5877d-439">String</span></span>|
|<span data-ttu-id="5877d-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="5877d-440">REMARKS</span></span>|<span data-ttu-id="5877d-441">String</span><span class="sxs-lookup"><span data-stu-id="5877d-441">String</span></span>|

### <a name="columns"></a><span data-ttu-id="5877d-442">資料行</span><span class="sxs-lookup"><span data-stu-id="5877d-442">Columns</span></span>

|<span data-ttu-id="5877d-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5877d-443">ColumnName</span></span>|<span data-ttu-id="5877d-444">DataType</span><span class="sxs-lookup"><span data-stu-id="5877d-444">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5877d-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5877d-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="5877d-446">String</span><span class="sxs-lookup"><span data-stu-id="5877d-446">String</span></span>|
|<span data-ttu-id="5877d-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="5877d-447">TABLE_OWNER</span></span>|<span data-ttu-id="5877d-448">String</span><span class="sxs-lookup"><span data-stu-id="5877d-448">String</span></span>|
|<span data-ttu-id="5877d-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-449">TABLE_NAME</span></span>|<span data-ttu-id="5877d-450">String</span><span class="sxs-lookup"><span data-stu-id="5877d-450">String</span></span>|
|<span data-ttu-id="5877d-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-451">COLUMN_NAME</span></span>|<span data-ttu-id="5877d-452">String</span><span class="sxs-lookup"><span data-stu-id="5877d-452">String</span></span>|
|<span data-ttu-id="5877d-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-453">DATA_TYPE</span></span>|<span data-ttu-id="5877d-454">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-454">Int16</span></span>|
|<span data-ttu-id="5877d-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-455">TYPE_NAME</span></span>|<span data-ttu-id="5877d-456">String</span><span class="sxs-lookup"><span data-stu-id="5877d-456">String</span></span>|
|<span data-ttu-id="5877d-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="5877d-457">PRECISION</span></span>|<span data-ttu-id="5877d-458">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-458">Int32</span></span>|
|<span data-ttu-id="5877d-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="5877d-459">LENGTH</span></span>|<span data-ttu-id="5877d-460">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-460">Int32</span></span>|
|<span data-ttu-id="5877d-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="5877d-461">SCALE</span></span>|<span data-ttu-id="5877d-462">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-462">Int16</span></span>|
|<span data-ttu-id="5877d-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="5877d-463">RADIX</span></span>|<span data-ttu-id="5877d-464">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-464">Int16</span></span>|
|<span data-ttu-id="5877d-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5877d-465">NULLABLE</span></span>|<span data-ttu-id="5877d-466">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-466">Int16</span></span>|
|<span data-ttu-id="5877d-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="5877d-467">REMARKS</span></span>|<span data-ttu-id="5877d-468">String</span><span class="sxs-lookup"><span data-stu-id="5877d-468">String</span></span>|
|<span data-ttu-id="5877d-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5877d-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="5877d-470">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-470">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="5877d-471">程序</span><span class="sxs-lookup"><span data-stu-id="5877d-471">Procedures</span></span>

|<span data-ttu-id="5877d-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5877d-472">ColumnName</span></span>|<span data-ttu-id="5877d-473">DataType</span><span class="sxs-lookup"><span data-stu-id="5877d-473">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5877d-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5877d-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="5877d-475">String</span><span class="sxs-lookup"><span data-stu-id="5877d-475">String</span></span>|
|<span data-ttu-id="5877d-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="5877d-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="5877d-477">String</span><span class="sxs-lookup"><span data-stu-id="5877d-477">String</span></span>|
|<span data-ttu-id="5877d-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="5877d-479">String</span><span class="sxs-lookup"><span data-stu-id="5877d-479">String</span></span>|
|<span data-ttu-id="5877d-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="5877d-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="5877d-481">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-481">Int16</span></span>|
|<span data-ttu-id="5877d-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="5877d-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="5877d-483">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-483">Int16</span></span>|
|<span data-ttu-id="5877d-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="5877d-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="5877d-485">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-485">Int16</span></span>|
|<span data-ttu-id="5877d-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="5877d-486">REMARKS</span></span>|<span data-ttu-id="5877d-487">String</span><span class="sxs-lookup"><span data-stu-id="5877d-487">String</span></span>|
|<span data-ttu-id="5877d-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="5877d-489">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-489">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="5877d-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5877d-490">ProcedureColumns</span></span>

|<span data-ttu-id="5877d-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5877d-491">ColumnName</span></span>|<span data-ttu-id="5877d-492">DataType</span><span class="sxs-lookup"><span data-stu-id="5877d-492">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5877d-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5877d-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="5877d-494">String</span><span class="sxs-lookup"><span data-stu-id="5877d-494">String</span></span>|
|<span data-ttu-id="5877d-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="5877d-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="5877d-496">String</span><span class="sxs-lookup"><span data-stu-id="5877d-496">String</span></span>|
|<span data-ttu-id="5877d-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="5877d-498">String</span><span class="sxs-lookup"><span data-stu-id="5877d-498">String</span></span>|
|<span data-ttu-id="5877d-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-499">COLUMN_NAME</span></span>|<span data-ttu-id="5877d-500">String</span><span class="sxs-lookup"><span data-stu-id="5877d-500">String</span></span>|
|<span data-ttu-id="5877d-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-501">COLUMN_TYPE</span></span>|<span data-ttu-id="5877d-502">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-502">Int16</span></span>|
|<span data-ttu-id="5877d-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-503">DATA_TYPE</span></span>|<span data-ttu-id="5877d-504">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-504">Int16</span></span>|
|<span data-ttu-id="5877d-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-505">TYPE_NAME</span></span>|<span data-ttu-id="5877d-506">String</span><span class="sxs-lookup"><span data-stu-id="5877d-506">String</span></span>|
|<span data-ttu-id="5877d-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="5877d-507">PRECISION</span></span>|<span data-ttu-id="5877d-508">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-508">Int32</span></span>|
|<span data-ttu-id="5877d-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="5877d-509">LENGTH</span></span>|<span data-ttu-id="5877d-510">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-510">Int32</span></span>|
|<span data-ttu-id="5877d-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="5877d-511">SCALE</span></span>|<span data-ttu-id="5877d-512">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-512">Int16</span></span>|
|<span data-ttu-id="5877d-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="5877d-513">RADIX</span></span>|<span data-ttu-id="5877d-514">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-514">Int16</span></span>|
|<span data-ttu-id="5877d-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5877d-515">NULLABLE</span></span>|<span data-ttu-id="5877d-516">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-516">Int16</span></span>|
|<span data-ttu-id="5877d-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="5877d-517">REMARKS</span></span>|<span data-ttu-id="5877d-518">String</span><span class="sxs-lookup"><span data-stu-id="5877d-518">String</span></span>|
|<span data-ttu-id="5877d-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="5877d-519">OVERLOAD</span></span>|<span data-ttu-id="5877d-520">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-520">Int32</span></span>|
|<span data-ttu-id="5877d-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5877d-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="5877d-522">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-522">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="5877d-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5877d-523">ProcedureParameters</span></span>

|<span data-ttu-id="5877d-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5877d-524">ColumnName</span></span>|<span data-ttu-id="5877d-525">DataType</span><span class="sxs-lookup"><span data-stu-id="5877d-525">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5877d-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="5877d-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="5877d-527">String</span><span class="sxs-lookup"><span data-stu-id="5877d-527">String</span></span>|
|<span data-ttu-id="5877d-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="5877d-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="5877d-529">String</span><span class="sxs-lookup"><span data-stu-id="5877d-529">String</span></span>|
|<span data-ttu-id="5877d-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="5877d-531">String</span><span class="sxs-lookup"><span data-stu-id="5877d-531">String</span></span>|
|<span data-ttu-id="5877d-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-532">COLUMN_NAME</span></span>|<span data-ttu-id="5877d-533">String</span><span class="sxs-lookup"><span data-stu-id="5877d-533">String</span></span>|
|<span data-ttu-id="5877d-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-534">COLUMN_TYPE</span></span>|<span data-ttu-id="5877d-535">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-535">Int16</span></span>|
|<span data-ttu-id="5877d-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-536">DATA_TYPE</span></span>|<span data-ttu-id="5877d-537">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-537">Int16</span></span>|
|<span data-ttu-id="5877d-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5877d-538">TYPE_NAME</span></span>|<span data-ttu-id="5877d-539">String</span><span class="sxs-lookup"><span data-stu-id="5877d-539">String</span></span>|
|<span data-ttu-id="5877d-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="5877d-540">COLUMN_SIZE</span></span>|<span data-ttu-id="5877d-541">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-541">Int32</span></span>|
|<span data-ttu-id="5877d-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5877d-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="5877d-543">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-543">Int32</span></span>|
|<span data-ttu-id="5877d-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="5877d-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="5877d-545">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-545">Int16</span></span>|
|<span data-ttu-id="5877d-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="5877d-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="5877d-547">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-547">Int16</span></span>|
|<span data-ttu-id="5877d-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5877d-548">NULLABLE</span></span>|<span data-ttu-id="5877d-549">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-549">Int16</span></span>|
|<span data-ttu-id="5877d-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="5877d-550">REMARKS</span></span>|<span data-ttu-id="5877d-551">String</span><span class="sxs-lookup"><span data-stu-id="5877d-551">String</span></span>|
|<span data-ttu-id="5877d-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="5877d-552">COLUMN_DEF</span></span>|<span data-ttu-id="5877d-553">String</span><span class="sxs-lookup"><span data-stu-id="5877d-553">String</span></span>|
|<span data-ttu-id="5877d-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5877d-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="5877d-555">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-555">Int16</span></span>|
|<span data-ttu-id="5877d-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="5877d-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="5877d-557">Int16</span><span class="sxs-lookup"><span data-stu-id="5877d-557">Int16</span></span>|
|<span data-ttu-id="5877d-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5877d-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="5877d-559">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-559">Int32</span></span>|
|<span data-ttu-id="5877d-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5877d-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="5877d-561">Int32</span><span class="sxs-lookup"><span data-stu-id="5877d-561">Int32</span></span>|
|<span data-ttu-id="5877d-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5877d-562">IS_NULLABLE</span></span>|<span data-ttu-id="5877d-563">String</span><span class="sxs-lookup"><span data-stu-id="5877d-563">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="5877d-564">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5877d-564">See also</span></span>

- [<span data-ttu-id="5877d-565">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="5877d-565">ADO.NET Overview</span></span>](ado-net-overview.md)
