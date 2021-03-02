---
title: matlplotlib
date: 2020-10-24 22:27:18
tags: 数据分析
categories: 学习笔记
---
# Numpy
1.numpy基于矩阵的运算
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt # sudo获取管理员权限

#array
# array = np.array([[1,2,3],   #列表→矩阵
#                   [4,5,6]])
# a=np.zeros((3,4))
# # b=np.ones((3,4))
# b=np.empty((2,3))
# print(b)
# print(a)
# print(array)
# print("number of dim:",array.ndim)#维度
# print("shape:",array.shape)#2行3列
# print("size:",array.size)#元素

# a=np.arange(6)#0-6
# print(a)
# a=np.arange(10,20,2) #有序数列，（起，末，间隔）
# print(a)
# b=np.arange(10).reshape((2,5))#0-10排列成2行5列
# print(b)
# c=np.linspace(1,10,5)#生成5段数列（线段）
# print(c)
# c=np.linspace(1,10,12).reshape((2,6))#6段一行数变成2行6列
# print(c)
#
# a=np.array([2,3,4,5])
# b=np.arange(4)
# e=np.arange(4).reshape((4,1))
# print(e)
# # c=b**2 #平方
# # print(c)
# # print(a,b)
# # d=a+b
# # print(d)
# # print(b)
# # f=a*b
# # print(f)
# f=a*e #逐个相乘
# print(f)
# f_dot=np.dot(a,b)
# f_dot_2=a.dot(b)
# print(f_dot)
# print(f_dot_2)
# e_dot=np.dot(a,e)
# print(e_dot)

# a=np.random.random((2,4))#随机生成0-1的数字组成2行4列的数列
# print(a)
# print(np.sum(a))
# print(np.min(a))
# print(np.max(a,axis=1))#按行找最大值
# print(np.max(a,axis=0))#按列找最大值

# A=np.arange(2,14).reshape((3,4))
#
# print(np.argmax(A))
# print(np.argmin(A))
# print(np.mean(A))
# print(A.mean())
# print(np.median(A))
# print(np.cumsum(A))
# print(np.diff(A))
# print(np.nonzero(A))#输出索引的行列

# A=np.arange(14,2,-1).reshape((3,4))
# print(A)
# print(np.sort(A))#逐行排序
# print(np.transpose(A))#转置
# print((A.T).dot(A))#矩阵乘法
# print(np.clip(A,5,9))#所有小于5的等于5，大于9的数等于9，中间的数保持不变
# print(np.mean(A,axis=0))#axis=0对矩阵中列进行计算，axis=1对行进行计算
#
# A=np.arange(3,15)
# print(A)
# B=A.reshape((3,4))
# print(B)
# print(A[2])
# print(B[2][1])#索引
# for row in B:
#     print(row)#按行输出
#
# for column in B.T:
#     print(column)#按列输出
#
# print('a',B.flatten())#矩阵变一行输出
# for item in B.flat:
#     print(item)#挨个输出

#合并
# A=np.array([1,1,1])#（3，）
# print(A.shape)
# B=np.array([2,2,2])
# C=np.vstack((A,B))#垂直合并
# print(C)
# print(A.shape,C.shape)
# D=np.hstack((A,B))#水平合并
# print(D,D.shape)
# t=A[np.newaxis,:]
# print(t)
# print(t.shape)#在行上加一个维度（1,3）
# f=B[:,np.newaxis]#在列上增加一个维度（3,1)
# print(f)
# print(f.shape)
# # print(f)
# # g=np.transpose(f)
# # print(g)
# w=np.concatenate((f,f),axis=0)#axis=0上下合并，axis=1左右合并
# print(w)

# #分割
# a= np.arange(12).reshape((3,4))
# # print(a)
#
# print(np.split(a,2,axis=1)) #把a按列对等分割成两块
# print(np.hsplit(a,2))#横向水平分割
# print(np.split(a,3,axis=0)) #把a按行对等分割成三块
# print(np.vsplit(a,3))#垂直纵向分割
# # print(np.array_split(a,3,axis=1))#把a按行任意分割成三块

# a=np.arange(4)
# print(a)
# b=a
# c=b
# a[0]=9
# print(a)
# print(c is not a)
# print(c)
# c[1:3]=[34,45]#改变第1到第3项即1，2项
# print(c)
# print(c)
#
# y=a.copy()  #只想copy值不想关联起来
# print(y)

#numpy序列化好的矩阵或序列；pandas字典形式的numpy
# s=pd.Series([1,3,6,np.nan,44,1])
# print(s)
# dates=pd.date_range('20201202',periods=6)
# print(dates)
# # 生成一个列表
# df=pd.DataFrame(np.random.randn(6,4),index=dates,columns=['a','b','c','d']) #行索引index=row,随便生成6行4列的数据,
# print(df)
# # df=pd.DataFrame(np.arange(12).reshape((3,4)))
# # print(df)
# df=pd.DataFrame({'A':1.,
#                  'B':pd.Timestamp('20201202'),
#                  'C':np.array([3]*4,dtype='int32'),
#                  'D':pd.Categorical(['test','train','test','train'])})
# print(df)#字典方式
# print(df.dtypes)#查看每列的数据形式
# # print(df._combine_match_columns())
# print(df.values)
# print(df.describe())#描述每行的均值，min等之类的
# print(df.T)
# print(df.sort_index(axis=1,ascending=False))#按列倒序排列
# print(df.sort_values(by='D'))#指定某个列进行排序
#
# dates=pd.date_range('20201202',periods=6)
# df=pd.DataFrame(np.arange(24).reshape((6,4)),index=dates,columns=['a','b','c','d'])
# print(df)
# # print(df['a'])
# # print(df.b)
# print(df[0:2])#=打印0-2行即1，2行
# print(df['20201202':'20201203'])#打印指定行
# print(df.loc['20201205'])
# print(df.loc[:,['a','c']])#打印指定列
# print(df.loc['20201203',['a','c']])#指定行的某几列

# print(df.iloc[3,1])#指定第3行，第1个数（包括0行0列）,通过位置选择
# print(df.iloc[3:5,1:2])#切片，打印第3行到第5行的第1列到第2列的数
# print(df.iloc[[3,5],1:3])


# pandas导入导出
# read_csv  read_excel  read_hdf  read_sql  read_json  msgpack  html gbq，stata，sas，clipboard，pickle
# to_csv to_excel.....
# date=pd.read_csv('student.csv')

# df1=pd.DataFrame(np.ones((3,3))*0,columns=['a','b','c'])
# df2=pd.DataFrame(np.ones((3,3))*1,columns=['a','b','c'])
# df3=pd.DataFrame(np.ones((3,3))*2,columns=['a','b','c'])
# print(df1)
# print(df2)
# print(df3)
# res=pd.concat([df1,df2,df3],axis=0)
# print(res)
# res2=pd.concat([df1,df2,df3],axis=1,ignore_index=True)#ignore_index序列从0-8不重复
# print(res2)

#inner，outer
# df1=pd.DataFrame(np.ones((3,4))*0,columns=['a','b','c','d'],index=[1,2,3])
# df2=pd.DataFrame(np.ones((3,4))*1,columns=['b','c','d','e'],index=[2,3,4])
# # print(df1)
# # print(df2)
# res=pd.concat([df1,df2])
# print(res)
# res=pd.concat([df1,df2],join='outer') # 并集
# print(res)
# res=pd.concat([df1,df2],join='inner',ignore_index=True) # 只保留两个表都有的列，即取交集
# print(res)
#
# df1=pd.DataFrame(np.ones((3,4))*0,columns=['a','b','c','d'],index=[1,2,3])
# df2=pd.DataFrame(np.ones((3,4))*1,columns=['b','c','d','e'],index=[2,3,4])
# res=pd.concat([df1,df2],axis=1,join_axes=[df1.index])#左右合并
# print(res)
# res2=pd.concat([df1,df2],axis=1)#左右合并
# print(res2)

# append
# df1=pd.DataFrame(np.ones((3,4))*0,columns=['a','b','c','d'])
# # df2=pd.DataFrame(np.ones((3,4))*1,columns=['a','b','c','d'])
# # df3=pd.DataFrame(np.ones((3,4))*2,columns=['a','b','c','d'])
# # res=df1.append([df2,df3],ignore_index=True) #多个列表叠加
# # res=df1.append([df2,df3])
# s1=pd.Series([1,2,3,4],index=['a','b','c','d']) #
# res=df1.append(s1,ignore_index=True)
# print(res)
#
# merge join类似
# l=pd.DataFrame({'key':['k0','k1','k2','k3'],
#                 'A':['A0','A1','A2','A3'],
#                 'B':['B0','B1','B2','B3']})
# r=pd.DataFrame({'key':['k0','k1','k2','k3'],
#                 'C':['C0','C1','C2','C3'],
#                 'D':['D0','D1','D2','D3']})
# print(l)
# print(r)
# res=pd.merge(l,r)#等值合并
# print(res)
# res2=pd.merge(l,r,on='key')
# print(res2)
# l=pd.DataFrame({'key1':['k0','k1','k2','k3'],
#                 'key2':['k0','k2','k1','k2'],
#                 'A':['A0','A1','A2','A3'],
#                 'B':['B0','B1','B2','B3']})
# r=pd.DataFrame({'key1':['k0','k1','k2','k3'],
#                 'key2':['k0','k1','k1','k1'],
#                 'C':['C0','C1','C2','C3'],
#                 'D':['D0','D1','D2','D3']})
# # print(l)
# # print(r)
# res=pd.merge(l,r,on=['key1','key2'],how='outer')#连接方法：how=inner交，outer并，right，left
# print(res)

# indicator       used in database  显示合并方式
# df1=pd.DataFrame({'col1':[0,1],'col_left':['a','b']}) # '表头、列名'
# df2=pd.DataFrame({'col1':[1,2,2],'col_right':[2,2,2]})
# print(df1)
# print(df2)
# res=pd.merge(df1,df2,on='col1',how='outer',indicator='indicator_column')
# print(res)
# #merge by index
# l=pd.DataFrame({'A':['A0','A1','A2'],
#                 'B':['B0','B1','B2']},
#                index=['K0','K1','K2'])
# r=pd.DataFrame({'C':['C0','C1','C2'],
#                 'D':['D0','D1','D2']},
#                index=['K0','K1','K3'])
# print(l)
# print(r)
# res=pd.merge(l,r,left_index=True,right_index=True,how='outer')  #按照索引来合并
# print(res)
# res2=pd.merge(l,r,left_index=True,right_index=True,how='inner')
# print(res2)

#handle overlapping
# boys=pd.DataFrame({'K':['K0','K1','K2'],'age':[1,2,3]})
# girls=pd.DataFrame({'K':['K0','K1','K2'],'age':[4,5,6]})
# print(boys)
# res=pd.merge(boys,girls,on='K',how='inner')
#
# # res=pd.merge(boys,girls,on='K',suffixes=['_boy','_girls'],how='inner')# suffixes后缀
# print(res)

# plot data
#Series
# data=pd.Series(np.random.randn(1000),index=np.arange(1000))
# data=data.cumsum()
# #DataFrame
# data=pd.DataFrame(np.random.randn(1000,4),
#                   index=np.arange(1000),
#                   columns=list('abcd'))
# data=data.cumsum()# 累加
# print(data.head())
# #展示方式：bar,box,area,scatter散点图,hexbin,hist，pie
# data.plot()
# ax=data.plot.scatter(x='a',y='b',color='DarkBlue',label='Class1')
# data.plot.scatter(x='a',y='c',color='DarkRed',label='Class2',ax=ax)  #ax=ax作用是两个scatter在一张图上
#
# plt.show()
#
# matplotlib
# import matplotlib.pyplot as plt
# import numpy as np
# x = np.linspace(-3,3,50)
# y1 = 2*x +1
# y2 = x**2
# # plt.figure(num=12,figsize=(10,10)) #所有对图的操作(图标figureX，图尺寸大小)
# # plt.figure()
# # plt.plot(x,y1,label='aaa')
# # plt.plot(x,y2,color='red',linewidth=3.0,linestyle='--',label='bbb') #具体某个函数，对所有线的操作
# # plt.legend(loc='best')
# l1, =plt.plot(x,y1,label='aaa')
# l2, =plt.plot(x,y2,color='red',linewidth=3.0,linestyle='--',label='bbb') #具体某个函数，对所有线的操作
# plt.legend(handles=[l1,l2],loc='best')#best,upper right,upper left,lower left,lower right,right,center left,center right,lower center,upper center,center

# # plt.xlim((-1,2)) # 规定x，y轴，没有则坐标轴自己规定
# # plt.ylim((-2,3))
# plt.xlabel('I am x')#定义坐标名称
# plt.ylabel('I am y')
#
# new_ticks=np.linspace(-1,3,4)#具体规定轴坐标间距
# plt.xticks(new_ticks)
# plt.yticks([-4,0,3,5],
#            [r'$dog$',r'$beaty\ cat$',r'$ \alpha$','big'])# 转义r,\+实际需要显示的，特殊需要加$
# # plt.show()

# gca=get current axis
# ax=plt.gca()
# ax.spines['right'].set_color('none')
# ax.spines['top'].set_color('none')
# ax.xaxis.set_ticks_position('bottom')
# ax.yaxis.set_ticks_position('left')
# ax.spines['bottom'].set_position(('data',0))
# ax.spines['left'].set_position(('data',0))
# plt.show()
# #
# import matplotlib.pyplot as plt
# import numpy as np
# x = np.linspace(-3,3,50)
# y = 2*x +1
# plt.figure(num=1,figsize=(8,5)) #所有对图的操作(图标figureX，图尺寸大小)
# plt.plot(x,y,linewidth=10) #plot线，scatter点
#
# ax=plt.gca()
# ax.spines['right'].set_color('none')
# ax.spines['top'].set_color('none')
# ax.xaxis.set_ticks_position('bottom')
# ax.yaxis.set_ticks_position('left')
# ax.spines['bottom'].set_position(('data',0))
# ax.spines['left'].set_position(('data',0))
#
# #坐标数字显示
# for label in ax.get_xticklabels()+ax.get_yticklabels():
#     label.set_fontsize(12)
#     label.set_bbox(dict(facecolor='white',edgecolor='None',alpha=0.7))
# plt.show()

# #标注
# x0=1
# y0=2*x0+1
# plt.scatter(x0,y0,s=50,color='b')#具体标注线上某个点
# x1=2
# y1=2*x1+1
# plt.scatter(x1,y1,color='r')#点
# plt.plot([x0,x0],[y0,0],'k--',lw=1.5)#（标注线的两个点x的坐标，y的坐标，线颜色类型，线宽）
# #annotation标注
# plt.annotate(r'$2*x+1=%s$'% y0,xy=(x0,y0),xycoords='data',xytext=(+30,-30),textcoords='offset points',fontsize=16,
#              arrowprops=dict(arrowstyle='->',connectionstyle='arc3,rad=.2')) #（label名称，坐标，基于数字，文本位置，位置基于，文字大小，方向线（类型，弧度角度））
# plt.text(-3.7,3,r'$this\ is\ the\ some\ text\ !$',fontdict={'size':16,'color':'r'})  #（说明文字的位置，内容）
# plt.show()
#
#漂亮散点图
# import matplotlib.pyplot as plt
# import numpy as np
# n=1024
# X=np.random.normal(0,1,n)#(平均值，方差，随机1024个数）
# Y=np.random.normal(0,1,n)
# Z=np.arctan2(Y,X)#点颜色值
# plt.scatter(X,Y,s=75,c=Z,alpha=0.5)#（点坐标，大小，颜色，透明度）
# # plt.scatter(np.arange(5),np.arange(5)) #(点随机生成的坐标）
# plt.xlim((-1.5,1.5))
# plt.ylim((-1.5,1.5))
# plt.xticks(())
# plt.yticks(())
# plt.show()

#条形图柱状图
#
# n=12
# X=np.arange(n)
# Y1=(1-X/float(n))*np.random.uniform(0.5,1.0,n)
# Y2=(1-X/float(n))*np.random.uniform(0.5,1.0,n)
# plt.bar(X,+Y1)#柱状图(坐标，颜色，边框颜色）
# plt.bar(X,-Y2)
#
# for x,y in zip(X,Y1):#(zip()每一步输出xy两个值）
#     plt.text(x,y,'%.2f'%y,ha='center',va='bottom')#(标注位置，值，横向居中对齐，纵向底部对齐）
#
# for x,y in zip(X,Y2):#(zip()每一步输出xy两个值）
#     plt.text(x,-y-0.05,'%.2f'%y,ha='center',va='top')
#
# plt.xlim((-0.5,n))#坐标轴首尾区间
# plt.xticks(())#不显示坐标系上的数
# plt.ylim(-1.25,1.25)
# plt.yticks(())
#
# plt.show()


#等高线图
# def f(x,y):
#     return (1-x/2+x**5+y**3)*np.exp(-x**2-y**2)
#
# n=256
# x=np.linspace(-3,3,n)
# y=np.linspace(-3,3,n)
# X,Y=np.meshgrid(x,y)#把xy绑定为网格输入值
#
# plt.contourf(X,Y,f(X,Y),8,alpha=0.7,cmap=plt.cm.hot)#填充登高区域（cmap=hot，cool），8代表填充8种颜色
# C=plt.contour(X,Y,f(X,Y),8,colors='black')#等高线的线
# plt.clabel(C,inline=True,fontsize=10)
#
# plt.xticks(())#要不要轴上的数字
# plt.yticks(())
# plt.show()

#图像显示
# a=np.array([0.3136,0.3653,0.4237,
#             0.3653,0.4396,0.5250,
#             0.4237,0.5250,0.6515]).reshape(3,3)
#
# plt.imshow(a,interpolation='nearest',cmap='bone',origin='upper')#（值，图像模糊还是清楚，origin=lower高在上，低在下）
# plt.colorbar(shrink=0.9) #色系说明
# plt.show()

# #3D数据
# from mpl_toolkits.mplot3d import Axes3D
#
# fig=plt.figure()
# ax=Axes3D(fig)
#
# X=np.arange(-4,4,0.25)
# Y=np.arange(-4,4,0.25)
# X,Y=np.meshgrid(X,Y)# 把xy等高线底面上去
# R=np.sqrt(X**2+Y**2)# 计算xy值
# Z=np.sin(R)# 3D中的高度值
#
# ax.plot_surface(X,Y,Z,rstride=1,cstride=1,cmap=plt.get_cmap('rainbow'))#（长，宽，高，线间距，，颜色）
# ax.contourf(X,Y,Z,zdir='z',offset=-2,cmap='rainbow')# 底下的等高线成面
# # ax.set_zlim(-2,2)
# plt.show()

# 一个图中显示好几个图，，，分格显示
# plt.figure()# 每一个图表的位置都按照它所画的网格来算就好了
# plt.subplot(2,2,2)#2行2列第个位置画一个图
# plt.plot([0,1],[0,1])
# plt.subplot(2,3,1)
# plt.plot([0,1],[0,1])
# plt.subplot(232)
# plt.plot([0,1],[0,3])
# plt.subplot(234)
# plt.plot([0,1],[0,4])
#
#
#
# plt.show()


# 图中图
#主次坐标轴

# animation动态图、
import numpy as np
from matplotlib import pyplot as plt
from matplotlib import animation
# from matplotlib.animation import FuncAnimation
fig,ax=plt.subplots()
x=np.arange(0,2*np.pi,0.01)
line, =ax.plot(x,np.sin(x))#sin图像，返回值是一个列表

def animate(i):
    line.set_ydata(np.sin(x+i/10))#updata范围大一点加快动画
    return line,

def init():
    line.set_ydata(np.sin(x))
    return line,

ani=animation.FuncAnimation(fig=fig,func=animate,frames=100,init_func=init,interval=20,blit=False)
#frames循环100个时间点，interval隔多少ms更新一次，blit是否更新所有点，FuncAnimation生成一个随时间变化的animation
plt.show()

```
