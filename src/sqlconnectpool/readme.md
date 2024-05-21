# ���ܸ���

�˴���ʵ������Դ��ȡ����ʼ�� (RAII) ģʽ������ʹ�����ӳع��� SQL ���ӡ� �������ֽ�һ�����Ĺ��ܣ�

1. **SqlConnPool��**��
    - ���� MySQL ���ӳء�
    - �ṩ��ʼ���ء���ȡ���ӡ��ͷ����ӡ��رճصķ�����
    - ��ʵ����һ�ֵ���ģʽ��`Instance()`������ȷ������������ֻ��һ�����ӳ�ʵ����

2. **SqlConnPool::Instance()**:
    - �ṩ��̬�������������ӳصĵ���ʵ����
    - ȷ��������һ�����ӳ�ʵ����

3. **SqlConnPool::Init()**:
    - ͨ������ָ�������� MySQL ���ӣ�`connSize`�������������ӵ���������ʼ�����ӳء�
    - ÿ�����Ӷ���ʹ�á�mysql_init()���͡�mysql_real_connect()�����������ġ�

4. **SqlConnPool::GetConn()**:
    - �ӳ��м��� MySQL ���ӡ�
    - �����Ϊ�գ������ȴ�ֱ�����ӿ��á�
    - ʹ���ź�����`sem_id`�������ƶԳصķ��ʣ�ȷ�������������������������������`Max_Conn`����

5. **SqlConnPool::FreeConn()**:
    - �� MySQL �����ͷŻسء�
    - �����ź���������ָʾ���ӿ��á�

6. **SqlConnPool::ClosePool()**:
    - ͨ���ͷ��������Ӳ�����`mysql_library_end()`���ر����ӳ�������MySQL��Դ��

7. **SqlConnPool::GetFreeConn()**:
    - ���س��е�ǰ���õĿ�����������

8. **SqlConnPool��������**��
    - ���á�ClosePool()����ȷ���ض�������ʱ������ȷ��������

9. **SqlConnRAII ��**��
    - ʵ�����ڹ��� SQL ���ӵ� RAII ģʽ��
    - ���乹�캯���д����ӳػ�ȡ���Ӳ����������������ͷ�����
    - ȷ������SqlConnRAII�����󳬳���Χʱ�Զ��ͷ����ӡ�

�ܵ���˵����δ����ṩ��һ�ְ�ȫ��Ч�ķ�����ʹ�����ӳ�������SQL���ӣ���ȷ����ȷ��ȡ���ͷ����ӣ�������Դй©��������ܡ�


# ǰ��֪ʶ

1. RAII(Resource Acquisition Is Initialization)
   RAII ����ĺ���˼���ǽ���Դ�������ڴ���䡢�ļ���������ݿ����ӡ����ȣ���������������������������ϵ��������Դ�ڶ����ʼ���ڼ��ȡ�����ڶ��󳬳���Χʱ�Զ��ͷţ�ͨ���������������У�����ȷ���˼�ʹ�����쳣����ǰ���أ���ԴҲ�ܿɿ����Զ����ͷš�
2. ����ģʽ
   - [�Ҹ����Թٽ����˵���ģʽ�������������˴�Ĵָ��](https://blog.csdn.net/weixin_41949328/article/details/107296517?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171575389116800180696112%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171575389116800180696112&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-107296517-null-null.142^v100^control&utm_term=%E5%8D%95%E4%BE%8B%E6%A8%A1%E5%BC%8F&spm=1018.2226.3001.4187)
3. sem
   - [�߳�ͬ�����Ʒ�װ��](https://mp.weixin.qq.com/s?__biz=MzAxNzU2MzcwMw==&mid=2649274278&idx=3&sn=5840ff698e3f963c7855d702e842ec47&chksm=83ffbefeb48837e86fed9754986bca6db364a6fe2e2923549a378e8e5dec6e3cf732cdb198e2&scene=0&xtrack=1#rd)
4. C++����MySQL
   - [C/C++ ʹ�� MySQL API ���� ���ݿ�](https://juejin.cn/post/7141190286838857735)