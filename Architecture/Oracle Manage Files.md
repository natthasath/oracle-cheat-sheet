# Oracle Manage Files
Oracle Manage Files (OMF) จะเป็นตัวจัดการไฟล์ในระดับ Object Level เมื่อเราทำการสร้างออบเจ็กต์ เช่น สร้าง Tablespace ตัว OMF จะเป็นตัวจัดการชื่อและไดเรกทอรี่ของ Datafile ให้โดยอัตโนมัติ โดยใช้ระบบไฟล์มาตรฐานของ Oracle Database แต่จะไม่สามารถใช้กับไฟล์ เช่น Trace File, Audit File, Alert Log และ Core File และยังสามารถทำงานร่วมกับ

#### Note: Automatic Storage Management (ASM)
ในการทำ Extend File System และ Volume Manager ตัว OMF สามารถทำได้โดยอัตโนมัติ แต่กับระบบที่เป็น ASM จะเพิ่มความสามารถในการทำ Striping (RAID), Software Mirroring และ Dynamic Storage Configuration โดยไม่จำเป็นต้องเสียเงินซื้อ Third-Party ที่เป็น Logical Volume Manager

# Table of ContentLVM
* Standard File System
* Pros and Cons

## Standard File System
* Tablespace
* Redo Log File
* Control File
* Archived Log
* Block Change Tracking File
* Flashback Log
* RMAN Backup

## Pros and Cons
* ลดความผิดพลาดการการตั้งชื่อไฟล์และไดเรกทอรี่
* ลดเวลาการทำงาน ไม่ต้องเสียเวลามานั่งจัดการไฟล์
* ลดความผิดพลาดจากการ Deleting, Overwriting
* ลดพื้นที่การใช้งาน Disk Space เนื่องจากทำงานในระดับ Object Level เมื่อมีการลบ Tablespace จะลบไฟล์ที่เกี่ยวข้องด้วยอัตโนมัติ (Obsolete Files)
* สามารถทำงานร่วมกับ LVM ได้

## Credit
https://docs.oracle.com/cd/B28359_01/server.111/b28310/omf.htm#i1007206
http://www.dba-oracle.com/real_application_clusters_rac_grid/omf.html