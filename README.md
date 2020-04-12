# ThreadPool
A C++ 11 Simple ThreadPool

## concerned libs:
iostream/vector/thread/deque/mutex/condition_variable/chrono

## basic idea 
构造线程容器，关联函数的操作为：
start()
threadLoop(); // 档线程开始工作时，循环调用get，只到获取到任务，开始执行
addTask(); // deque中增加任务，每新增一个进行notify_one操作唤醒工作线程
get(); // 获取unique_lock锁，循环 读取队列，若队列为空，则wait(lck)，直至新增任务将改线程唤醒
stop(); // 线程清理工作，join() delete 等
