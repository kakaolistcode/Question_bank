from tkinter import *
from tkinter.messagebox import *
from tkinter import scrolledtext,StringVar
from datetime import datetime
from tkinter import filedialog
import random,os
from PIL import Image,ImageTk
from concurrent.futures import ThreadPoolExecutor
class GuessGui:
    def __init__(self, title):
        if os.path.exists('Wrongquestion'):
            pass
        else:
            os.mkdir('Wrongquestion')

        if not os.path.exists('Wrongquestion/' + self.getNowTimeString().split(' ')[0] + '.txt'):
            open('Wrongquestion/' + self.getNowTimeString().split(' ')[0] + '.txt', 'w', encoding='utf-8')
        self.nowfile='H3CNE1.txt'
        self.type=['first',1]
        self.is_open=''
        self.picturename=os.listdir('Txt')
        self.root = Tk()
        self.root.title(title)
        self.root.geometry('1400x800')
        self.nowtime=StringVar()
        self.nowtime.set(self.getNowTimeString())
        self.change=StringVar()
        self.up=StringVar()
        self.up1=StringVar()
        self.down=StringVar()
        self.down1=StringVar()
        self.stone=StringVar()
        self.build_buttons_first()
        # self.killButton()
        self.A=0
        self.B=0
        self.C=0
        self.D=0
        self.E=0
        self.F=0
        self.number=0
        self.questionmod=0
        self.numbers=100
        self.model=''
    def build_buttons_first(self):
        self.bu07=Label(self.root)
        self.bu02=Label(self.root)
        self.bu03=Label(self.root)
        self.bu04=Label(self.root)
        self.bu01=Label(self.root)
        self.bu05=Label(self.root)
        self.bu06=Label(self.root)
        self.bu_tixing01=Label(self.root)
        self.bu_tixing02=Label(self.root)
        self.bu_tixing03=Label(self.root)
        self.bu_tixing04=Label(self.root)
        self.bu_tixing05=Label(self.root)
        self.bu_tixing06=Label(self.root)
        self.bu_tixing07=Label(self.root)
        self.bu_tixing010=Label(self.root)
        self.timer=Label(self.root)
        self.food=Label(self.root)
        self.group=Label(self.root)
        self.forknowlege=Label(self.root)
        self.content=Label(self.root)
        self.speedofprogress=Label(self.root)
        self.group1=Label(self.root)
    def findtitle(self):
        f1=''
        f=self.file
        for i in range(len(f)):
            if f[i:i + 8] == 'QUESTION':
                for j in range(i+8,len(f),1):
                    if f[j]=='\n':
                        # print(i,j,f[i + 8:j])
                        f1 += f[i + 8:j].replace('\n', '')+' '
                        break
        f1=list(f1.split(' '))
        # print(f1)
        for i in range(len(f1)):
            for j in f1[i]:
                # print(j)
                if j in '0123456789':
                    continue
                else:
                    f1[i] = f1[i].replace(j, '')
        del f1[len(f1)-1]
        self.num=[int(i) for i in f1]
    def screen(self):
        self.switch_page()
        self.model='anwser'
        self.nums=-1
        if os.path.exists('Wrongquestion/'+self.getNowTimeString().split(' ')[0]+'.txt'):
            self.file=open('Wrongquestion/'+self.getNowTimeString().split(' ')[0]+'.txt','r',encoding='utf-8').read()
        self.findtitle()
        print(len(self.num))
        self.rightorerror = [0 for i in range(len(self.num))]
        self.build_buttons_of_screen()
        self.image=Button(self.root,font=("黑体",18),text="图片",width=20,height=2,relief=GROOVE,background="#ffffd2",command=self.showpicture)
        self.image.place(relx=.75,rely=.7)
        self.group =Frame(self.root, padx=5, pady=5,bg='#1ffff8',border=0)
        self.group.place(relx=.001,rely=.05,height=550,width=960)
        self.food = LabelFrame(self.root, text="解析", font=('黑体',15),pady=5, padx=5,bg='#fffff8',border=0)
        self.food.place(relx=.71, rely=.045, relwidth=.5, relheight=.6)
        self.forknowlege = Message(self.food, textvariable=self.up, font=('黑体',17),anchor='w',bg='#fffffb')
        self.forknowlege.grid(row=0, column=0, sticky='nw')
        self.xscroll=Scrollbar(self.group,orient=HORIZONTAL)
        self.xscroll.pack(side=BOTTOM,fill=X)
        self.yscroll=Scrollbar(self.group)
        self.yscroll.pack(side=RIGHT,fill=Y)
        self.content = Text(self.group,font=('黑体',17),bg='#fffffc',xscrollcommand=self.xscroll.set,yscrollcommand=self.yscroll.set)
        self.content.place(width=930,height=520)
        self.yscroll.config(command=self.content.yview)
        self.xscroll.config(command=self.content.xview)
        self.next1()
    def build_Main(self):
        self.root.configure(bg="#f8e0bd")
    def updata_text(self,*args):
        self.board.delete('1.0',"end")
        self.board.insert('insert',open(self.nowfile,encoding='utf-8',mode='r').read())
    def updata_wrong_text(self,*args):
        self.board1.delete('1.0',"end")
        self.board1.insert("insert",open('Wrongquestion/' + self.getNowTimeString().split(' ')[0] + '.txt',mode='r',encoding='utf-8').read())
    def click(self):
        self.filechoice=filedialog.askopenfilename()
        if self.nowfile!=self.filechoice:
            self.change.set("已选择的文件是:" + self.filechoice.split('/')[-1])
            self.nowfile = self.filechoice
            self.updata_text()
        elif self.filechoice=='':
            pass
        # self.changefile.configure(bg='white')
    def kill_first_type(self,a=1):
        self.beenopenfile.destroy()
        self.changefile.destroy()
        self.detail_show.destroy()
        self.fram.destroy()
        self.yscroll.destroy()
        self.board.destroy()
        self.rect1.destroy()
        self.test.destroy()
        self.rect2.destroy()
        self.test1.destroy()
        self.test2.destroy()
        self.detail_show1.destroy()
        self.show_wrong.destroy()
        self.yscroll1.destroy()
        self.board1.destroy()
    def first_type(self):
        self.type[0]='first'
        self.beenopenfile=Label(self.root,textvariable=self.change,font=self.font,bg='#f8e0c9',anchor="w")
        self.beenopenfile.place(x=100,y=75,width=450,height=50)
        self.change.set("已选择的文件是:"+self.nowfile)
        self.changefile=Button(self.root,text='切换文件',font=self.font,command=self.click,relief=FLAT,bg='#f8cdbc',border=0)
        self.changefile.place(x=455,y=75,width=100,height=50)
        self.detail_show=Label(self.root,font=self.font,bg='#f2b9b7',text="文件内容预览",anchor="w")
        self.detail_show.place(x=100,y=150,height=50,width=150)
        self.detail_show.bind('<Double-Button>',self.updata_text)
        self.fram=Frame(self.root,bg='white')
        self.fram.place(width=600,height=580,x=100,y=200)
        self.yscroll = Scrollbar(self.fram,)
        self.board=Text(self.fram,bg="#f8e1ca",font=("幼圆",14),relief=FLAT,yscrollcommand=self.yscroll.set)
        self.board.place(width=585,height=580)
        self.yscroll.pack(side=RIGHT, fill=Y)
        self.yscroll.config(command=self.board.yview)
        self.rect1=Canvas(self.root,highlightthickness=0,bg='#f8e0ca')
        self.rect1.place(x=800,y=0,width=600,height=325)
        self.test=Button(self.rect1,text="基础模拟测试",font=self.font,bg='#f8eada',highlightthickness=0,border=0,command=lambda *args:(self.kill_first_type(1),self.build_content()))
        self.test.place(x=0,y=35,width=270,height=50)
        self.test1=Button(self.rect1,text='基础顺序测试',font=self.font,bg='#f8eada',highlightthickness=0,border=0)
        self.test1.place(x=0,y=125,width=330,height=50)
        self.test2 = Button(self.rect1, text='基础错题训练', font=self.font, bg='#f8eada', highlightthickness=0,
                            border=0)
        self.test2.place(x=0, y=210, width=390, height=50)
        self.rect2=Canvas(self.rect1,bg='#f2b9b2',highlightthickness=0)
        self.rect2.place(x=0,y=300,width=600,height=25)
        self.detail_show1=Label(self.root,text='错题预览',bg='#f4b9b2',font=self.font)
        self.detail_show1.place(x=775,y=375,width=100,height=50)
        self.detail_show1.bind('<Double-Button>',self.updata_wrong_text)
        self.show_wrong=Frame(self.root,bg='white')
        self.show_wrong.place(x=750,y=425,height=365,width=640)
        self.yscroll1=Scrollbar(self.show_wrong)
        self.yscroll1.pack(side=RIGHT, fill=Y)
        self.board1=Text(self.show_wrong,bg="#f8e1ca",font=('幼圆',15),relief=GROOVE,yscrollcommand=self.yscroll1.set)
        self.board1.place(x=0,y=0,width=625,height=365)
        self.yscroll1.config(command=self.board1.yview)
        self.updata_wrong_text()
        self.updata_text()
    def second_type(self):
        self.type[0]='second'
    def third_type(self):
        self.type[0]='third'
    def relase_1(self):
        self.show_wrong.destroy()
        self.beenopenfile.destroy()
        self.fram.destroy()
        self.rect1.destroy()
        self.changefile.destroy()
        self.detail_show1.destroy()
        self.detail_show.destroy()
    def relase_2(self):
        pass
    def relase_3(self):
        pass
    def enter_section_1(self,*args):
        self.section_1.config(bg='#fbf2e3')
        self.type[1]=1
    def leave_section_1(self,*args):
        self.section_1.config(bg='#f9e9cd')
    def enter_section_2(self,*args):
        self.section_2.config(bg='#fbf2e3')
        self.type[1]=2
    def leave_section_2(self,*args):
        self.section_2.config(bg='#f9e9cd')
    def enter_section_3(self,*args):
        self.section_3.config(bg='#fbf2e3')
        self.type[1]=3
    def leave_section_3(self,*args):
        self.section_3.config(bg='#f9e9cd')
    def changing_over(self,*args):
        if self.type[0]=='first':
            self.relase_1()
        elif self.type[0]=='second':
            self.relase_2()
        elif self.type[0]=='third':
            self.relase_3()
        if self.type[1]==1:
            self.first_type()
        elif self.type[1]==2:
            self.second_type()
        elif self.type[1]==3:
            self.third_type()
    def killButton2(self):
        self.canvas_rect.destroy()
        self.section_1.destroy()
        self.section_2.destroy()
        self.section_3.destroy()
        self.kill_first_type()
    def build_home(self):
        self.font=("幼圆",17)
        self.switch_page()
            # print(2)
        self.model="home"
        self.canvas_rect=Canvas(self.root,bg='#f9e9cd',highlightthickness=0)
        self.canvas_rect.place(relx=0,rely=0,width=100,height=800)
        self.canvas_rect.create_rectangle(0,0,100,800,fill='#f9e9cd',outline='#f8e0b0')
        self.section_1=Label(self.canvas_rect,text='首页',font=self.font,bg='#f9e9cd')
        self.section_1.place(relx=0,rely=.05,width='100',height='50')
        self.section_1.bind("<Enter>",self.enter_section_1)
        self.section_1.bind("<Leave>",self.leave_section_1)
        self.section_1.bind("<ButtonRelease-1>",self.changing_over)
        self.section_2 = Label(self.canvas_rect, text='文件', font=("幼圆", 17), bg='#f9e9cd')
        self.section_2.place(relx=0, rely=.15, width='100', height='50')
        self.section_2.bind("<Enter>", self.enter_section_2)
        self.section_2.bind("<Leave>", self.leave_section_2)
        self.section_2.bind("<ButtonRelease-1>",self.changing_over)
        self.section_3 = Label(self.canvas_rect, text='设置', font=("幼圆", 17), bg='#f9e9cd')
        self.section_3.place(relx=0, rely=.25, width='100', height='50')
        self.section_3.bind("<Enter>", self.enter_section_3)
        self.section_3.bind("<Leave>", self.leave_section_3)
        self.section_3.bind("<ButtonRelease-1>",self.changing_over)
        # print(type(self.type))
        # if self.type[0]=='first':
        self.first_type()
        # self.input_1=Text(self.root,font=('黑体',18),relief=FLAT)
        # self.input_1.place(width='600',height='50',relx=.1,rely=.05)
    def build_menu(self):
        root_menu = Menu(self.root)
        root_menu.configure(bg='#fffff5')
        file_menu = Menu(root_menu)
        file_menu.configure(bg='#fffff3')
        root_menu.add_cascade(label="菜单", menu=file_menu)
        file_menu.add_command(label="错题集",command=self.screen)
        file_menu.add_command(label="模拟考试",command=self.build_content)
        # file_menu.add_separator() #增加分割线
        file_menu.add_command(label="返回", command=self.build_home)
        # file_menu.add_command(label='删除',command=lambda :os.remove("Wrongquestion/"+self.getNowTimeString().split(' ')[0]+".txt"))
        self.root.config(menu=root_menu)
        # self.build_home()
        # self.screen()
        # self.build_content()
    def build_timer(self):
        self.minute=60
        self.second=0
        self.timer = Label(self.root,font=('times', 20),textvariable=self.nowtime,fg='red',bg='#fffff8')
        self.timer.grid(row=0, columnspan=3)
        self.updateTime()
    def updateTime(self):
        if self.second ==0 and self.minute==0:
            self.submit()
        if self.second==0:
            self.second=59
            self.minute-=1
        else:
            self.second-=1
        self.nowtime.set(str(self.minute)+':'+('0' if self.second<10 else '')+str(self.second))
        self.timer.after(1000, self.updateTime)
    def ready_picture(self):
        self.is_ready=[]
        if self.model=='question':
            for i in range(len(self.picturename)):
                en = eval(self.picturename[i].replace('-(0).png', '').replace('-(1).png', '').replace('-(2).png', ''))
                # print(en)
                for j in en:
                    if self.num[self.nums] == j:
                        self.is_ready=[i]
                        return 0
        elif self.model=='anwser':
            print(self.num,self.nums)
            for i in range(len(self.picturename)):
                en = eval(self.picturename[i].replace('-(0).png', '').replace('-(1).png', '').replace('-(2).png', ''))
                # print(en)
                for j in en:
                    if self.num[self.nums] == j:
                        self.is_ready = [i]
                        return 0
    def opened(self):
        try:
            self.is_open=0
            self.image.destroy()
        except:
            pass
    def displaypicture(self, root, path):
        def resize(w, h, w_box, h_box, pil_image):
            '''
            resize a pil_image object so it will fit into
            a box of size w_box times h_box, but retain aspect ratio
            对一个pil_image对象进行缩放，让它在一个矩形框内，还能保持比例
            '''
            f1 = 1.0 * w_box / w  # 1.0 forces float division in Python2
            f2 = 1.0 * h_box / h
            factor = min([f1, f2])
            # print(f1, f2, factor) # test
            # use best down-sizing filter
            width = int(w * factor)
            height = int(h * factor)
            return pil_image.resize((width, height), Image.ANTIALIAS)

        # size of image display box you want
        # 期望图像显示的大小
        w_box = 800
        h_box = 800

        # open as a PIL image object
        # 以一个PIL图像对象打开
        pil_image = Image.open(path)

        # get the size of the image
        # 获取图像的原始大小
        w, h = pil_image.size

        # resize the image so it retains its aspect ration
        # but fits into the specified display box
        # 缩放图像让它保持比例，同时限制在一个矩形框范围内
        pil_image_resized = resize(w, h, w_box, h_box, pil_image)

        # convert PIL image object to Tkinter PhotoImage object
        # 把PIL图像对象转变为Tkinter的PhotoImage对象
        tk_image = ImageTk.PhotoImage(pil_image_resized)

        # put the image on a widget the size of the specified display box
        # Label: 这个小工具，就是个显示框，小窗口，把图像大小显示到指定的显示框
        label = Label(root, image=tk_image, width=w_box, height=h_box)
        # padx,pady是图像与窗口边缘的距离
        label.pack(padx=5, pady=5)
        root.mainloop()
    def showpicture(self):
        # print(self.picturename[self.is_ready[0]])
        if self.is_ready==[] or self.is_open==1:
            print('s',self.is_open,self.is_ready)
            return 0
        else:
            self.is_open=1
            self.image=Toplevel()
            self.image.title("可能的图片")
            self.image.protocol("WM_DELETE_WINDOW",self.opened)
            print(self.picturename[self.is_ready[0]])
            self.displaypicture(root=self.image,path=f"Txt/{self.picturename[self.is_ready[0]]}")
            self.image.mainloop()
        #self.num[self.nums]
    def build_content(self):
        self.switch_page()
        self.model='question'
        self.file = open(self.nowfile,"r",encoding='utf-8').read()
        # print(self.file)
        self.grade=0
        self.build_buttons_of_content()
        self.build_timer()
        print(self.nowtime.get())
        self.rightorerror=[0 for i in range(self.numbers)]
        self.number=0
        self.speedofprogress=Label(self.root,textvariable=self.stone,fg='purple',bg='#fffff8')
        self.speedofprogress.grid(column=4,row=0,sticky='en')
        self.nums=-1
        self.num = [random.randint(1, 3564) for i in range(self.numbers)]
        self.anwser=0
        print(self.num)
        self.image=Button(self.root,font=("黑体",18),text="图片",width=20,height=2,relief=GROOVE,background="#ffffd2",command=self.showpicture)
        self.image.place(relx=.75,rely=.7)
        self.group1 = Frame(self.root, padx=5, pady=5,bg='#fffff8',border=0)
        self.group1.place(relx=.001,rely=.05,height=600,width=960)
        self.food=LabelFrame(self.root,text="解析:",font=("黑体",15),pady=5,padx=5,bg='#fffff9',border=0)
        self.food.place(relx=.7,rely=.045,relwidth=.5,relheight=.6)
        self.forknowlege=Message(self.food,font=("黑体",17),textvariable=self.up,anchor='w',relief='flat',bg='#fffff7')
        self.forknowlege.grid(row=0,column=0,sticky='nw')
        self.root.rowconfigure(1, weight=1)
        self.root.columnconfigure(0, weight=1)
        self.group1.rowconfigure(0, weight=1)
        self.group1.columnconfigure(0, weight=1)
        self.xscroll=Scrollbar(self.group1,orient=HORIZONTAL)
        self.xscroll.pack(side=BOTTOM,fill=X)
        self.yscroll=Scrollbar(self.group1)
        self.yscroll.pack(side=RIGHT,fill=Y)
        self.content = Text(self.group1,font=("黑体",20),bg='#fffff8',xscrollcommand=self.xscroll.set,yscrollcommand=self.yscroll.set,border=0)
        self.content.place(height=540,width=930)
        self.yscroll.config(command=self.content.yview)
        self.xscroll.config(command=self.content.xview)
        self.next()
    def getNowTimeString(self, mode=None):
        now = datetime.now()
        if mode == 'start':
            self.begin = now
        elif mode == 'stop':
            self.end = now
        text = '%s-%s-%s %s:%s:%s' % \
               (now.year,
                '{:0>2d}'.format(now.month),
                '{:0>2d}'.format(now.day),
                '{:0>2d}'.format(now.hour),
               '{:0>2d}'.format(now.minute),
                '{:0>2d}'.format(now.second))
        return text
    def rightA(self):
        if self.A==0 and self.questionmod==0:
            self.A=1
            self.B=0
            self.C=0
            self.D=0
            self.bu_tixing02.configure(fg='black')
            self.bu_tixing03.configure(fg='black')
            self.bu_tixing04.configure(fg='black')
        elif self.A==1 and self.questionmod==0:
            self.A=0
            self.D=0
            self.C=0
            self.D=0
        elif self.A==0 and self.questionmod==1:
            self.A=1
        elif self.A==1 and self.questionmod==1:
            self.A=0
        if self.A==1:
            self.bu_tixing01.configure(fg='red',background="#ffffa5")
        else:
            self.bu_tixing01.configure(fg='black',background="#ffffd2")
    def rightB(self):
        if self.B == 0 and self.questionmod == 0:
            self.A = 0
            self.B = 1
            self.C = 0
            self.D = 0
            self.bu_tixing01.configure(fg='black')
            self.bu_tixing03.configure(fg='black')
            self.bu_tixing04.configure(fg='black')
        elif self.B == 1 and self.questionmod == 0:
            self.A = 0
            self.B = 0
            self.C = 0
            self.D = 0
        elif self.B==0 and self.questionmod==1:
            self.B=1
        elif self.B==1 and self.questionmod==1:
            self.B=0
        if self.B == 1:
            self.bu_tixing02.configure(fg='red',background="#ffffa5")
        else:
            self.bu_tixing02.configure(fg='black',background="#ffffd2")
    def rightC(self):
        if self.C == 0 and self.questionmod == 0:
            self.A = 0
            self.B = 0
            self.C = 1
            self.D = 0
            self.bu_tixing01.configure(fg='black')
            self.bu_tixing02.configure(fg='black')
            self.bu_tixing04.configure(fg='black')
        elif self.C == 1 and self.questionmod == 0:
            self.A = 0
            self.D = 0
            self.C = 0
            self.D = 0
        elif self.C==0 and self.questionmod==1:
            self.C=1
        elif self.C==1 and self.questionmod==1:
            self.C=0
        if self.C == 1:
            self.bu_tixing03.configure(fg='red',background="#ffffa5")
        else:
            self.bu_tixing03.configure(fg='black',background="#ffffd2")
    def rightD(self):
        if self.D == 0 and self.questionmod == 0:
            self.A = 0
            self.B = 0
            self.C = 0
            self.D = 1
            self.bu_tixing01.configure(fg='black')
            self.bu_tixing03.configure(fg='black')
            self.bu_tixing02.configure(fg='black')
        elif self.D == 1 and self.questionmod == 0:
            self.A = 0
            self.D = 0
            self.C = 0
            self.D = 0
        elif self.D==0 and self.questionmod==1:
            self.D=1
        elif self.D==1 and self.questionmod==1:
            self.D=0
        if self.D == 1:
            self.bu_tixing04.configure(fg='red',background="#ffffa5")
        else:
            self.bu_tixing04.configure(fg='black',background="#ffffd2")
    def switch_page(self):
        match self.model:
            case "question":
                self.killbutton1()
            case "anwser":
                self.killButton()
            case "home":
                self.killButton2()
    def findanwser(self):
        if self.questionmod:
            end=''
            if self.A==1:
                end+='A'
            if self.B==1:
                end+='B'
            if self.C==1:
                end+='C'
            if self.D==1:
                end+='D'
            print(end)
            return end
        else:
            if self.A==1:
                return 'A'
            elif self.B==1:
                return 'B'
            elif self.C==1:
                return 'C'
            elif self.D==1:
                return 'D'
            else:
                return 1
    def confirm(self):
        print(self.anwser)
        if self.anwser == str(self.findanwser()):
            if self.rightorerror[self.nums]==0:
                self.grade+=1
                self.up.set('回答正确\n'+self.analysis)
                self.number += 1
            else:
                self.up.set(self.analysis)
        else:
            if self.rightorerror[self.nums]==0:
                self.rightorerror[self.nums]=1
                open('Wrongquestion/'+self.getNowTimeString().split(' ')[0]+'.txt','a',encoding='utf-8').write(self.nowquestion)
                self.up.set('回答错误\n'+self.analysis)
                self.number += 1
            else:
                self.up.set(self.analysis)
    def theprevious1(self):
        self.restore1()
        if self.nums!=0:
            self.nums-=1
        self.nowquestion=self.file[self.file.find("QUESTION"+str(self.num[self.nums])):self.file.find("QUESTION"+str(self.num[self.nums+1]))]
        self.word()
        self.ready_picture()
        self.up.set(self.analysis)
    def restore1(self):
        self.A = 0
        self.B = 0
        self.C = 0
        self.D = 0
        self.bu01.configure(fg='black',background="#ffffd2")
        self.bu02.configure(fg='black',background="#ffffd2")
        self.bu03.configure(fg='black',background="#ffffd2")
        self.bu04.configure(fg='black',background="#ffffd2")
    def restore(self):
        self.A = 0
        self.B = 0
        self.C = 0
        self.D = 0
        self.bu_tixing01.configure(fg='black',background="#ffffd2")
        self.bu_tixing03.configure(fg='black',background="#ffffd2")
        self.bu_tixing02.configure(fg='black',background="#ffffd2")
        self.bu_tixing04.configure(fg='black',background="#ffffd2")
    def confirm1(self):
        self.rightorerror[self.nums]=1
        self.up.set(self.analysis)
    def next1(self):
        self.restore1()
        if self.nums!=len(self.num)-1:
            self.nums+=1
        self.up.set('')
        print(self.num,self.nums,)
        self.nowquestion=self.file[self.file.find("QUESTION"+str(self.num[self.nums])):None if self.nums==len(self.num)-1 else self.file.find("QUESTION"+str(self.num[self.nums+1]))]
        # print(self.nowquestion)
        self.word()
        self.ready_picture()
        # self.nowquestion = self.file[self.file.find("QUESTION"):self.file[self.file.find("QUESTION")+8:].find(
        #     "QUESTION" )+self.file.find("QUESTION")]
        # self.word()
        if self.rightorerror[self.nums]!=0:
            self.up.set(self.analysis)
        else:
            self.up.set('')
    def next(self):
        self.restore()
        if self.nums!=len(self.rightorerror)-1:
            self.nums+=1
        print(self.nums,self.num[self.nums])
        self.stone.set(f'第{self.nums+1}题,完成数'+str(self.number+1)+'/100')
        self.nowquestion=self.file[self.file.find("QUESTION"+str(self.num[self.nums])):self.file.find("QUESTION"+str(self.num[self.nums]+1))]
        # self.opened()
        self.word()#输出题目和答案的字符串并且分割
        self.ready_picture()
        if self.rightorerror[self.nums]==0:
            self.up.set('')
        else:
            self.up.set(self.analysis)
    def theprevious(self):
        self.restore()
        print(self.nums)
        if self.nums!=0:
            self.nums-=1
        self.stone.set(f'第{self.nums+1}题,完成数'+str(self.number+1)+'/100')

        if self.rightorerror[self.nums]==0:
            self.up.set('')
        self.nowquestion=self.file[self.file.find("QUESTION"+str(self.num[self.nums])):self.file.find("QUESTION"+str(self.num[self.nums]+1))]
        self.word()
        self.ready_picture()
        if self.rightorerror[self.nums]!=0:
            self.up.set(self.analysis)
    def build_buttons_of_screen(self):
        self.bu_tixing01 = Button(self.root, text='A', font=("黑体",18),width=10, command=self.rightA,background="#ffffd2",relief=GROOVE)
        self.bu_tixing01.place(relx=.03,rely=.85)
        self.bu_tixing02 = Button(self.root, text='B', font=("黑体",18),width=10, command=self.rightB,background="#ffffd2",relief=GROOVE)
        self.bu_tixing02.place(relx=.15,rely=.85)
        self.bu_tixing03 = Button(self.root, text='C', font=("黑体",18),width=10, command=self.rightC,background="#ffffd2",relief=GROOVE)
        self.bu_tixing03.place(relx=.27,rely=.85)
        self.bu_tixing04 = Button(self.root, text='D', font=("黑体",18),width=10, command=self.rightD,background="#ffffd2",relief=GROOVE)
        self.bu_tixing04.place(relx=.39,rely=.85)
        self.bu05 = Button(self.root, text='确定',font=("黑体",18), width=10, command=self.confirm1,relief=GROOVE)
        self.bu05.place(relx=.55,rely=.85)
        self.bu06 = Button(self.root, text='上一题', font=("黑体",18),width=10, command=self.theprevious1,relief=GROOVE)
        self.bu06.place(relx=.71,rely=.85)
        self.bu07 = Button(self.root, text='下一题', font=("黑体",18),width=10, command=self.next1,relief=GROOVE)
        self.bu07.place(relx=.87,rely=.85)
    def killButton(self):
        self.bu07.destroy()
        self.bu06.destroy()
        self.bu05.destroy()
        self.bu_tixing04.destroy()
        self.bu_tixing03.destroy()
        self.bu_tixing02.destroy()
        self.bu_tixing01.destroy()
        self.food.destroy()
        self.forknowlege.destroy()
        self.content.destroy()
        self.group.destroy()
    def killbutton1(self):
        self.speedofprogress.destroy()
        self.group1.destroy()
        self.forknowlege.destroy()
        self.food.destroy()
        self.content.destroy()
        self.speedofprogress.destroy()
        self.timer.destroy()
        self.bu_tixing010.destroy()
        self.bu_tixing07.destroy()
        self.bu_tixing06.destroy()
        self.bu_tixing05.destroy()
        self.bu_tixing04.destroy()
        self.bu_tixing03.destroy()
        self.bu_tixing02.destroy()
        self.bu_tixing01.destroy()
    def build_buttons_of_content(self):
        self.bu_tixing01 = Button(self.root, font=("黑体",17),text='A', width=10,command=self.rightA,background="#cffdd2",relief=GROOVE)
        self.bu_tixing01.place(relx=.04,rely=.9)

        self.bu_tixing02 = Button(self.root, font=("黑体",17),text='B', width=10,command=self.rightB,background="#ffffd2",relief=GROOVE)
        self.bu_tixing02.place(relx=.15,rely=.9)

        self.bu_tixing03 = Button(self.root,font=("黑体",17), text='C', width=10,command=self.rightC,background="#ffffd2",relief=GROOVE)
        self.bu_tixing03.place(relx=.26,rely=.9)

        self.bu_tixing04 = Button(self.root,font=("黑体",17), text='D', width=10,command=self.rightD,background="#ffffd2",relief=GROOVE)
        self.bu_tixing04.place(relx=.37,rely=.9)
        # self.bu_tixing08 = Button(self.root,text='E',width=10,command=self.rightE)
        # self.bu_tixing08.grid
        # self.bu_tixing09 = Button(self.root,text='F',width=10,command=self.rightF)
        # self.bu_tixing09.grid
        self.bu_tixing05 = Button(self.root, font=("黑体",17),text='确定', width=10,command=self.confirm,relief=GROOVE)
        self.bu_tixing05.place(relx=.48,rely=.9)
        self.bu_tixing06 = Button(self.root, font=("黑体",17),text='上一题', width=10,command=self.theprevious,relief=GROOVE)
        self.bu_tixing06.place(relx=.59,rely=.9)
        self.bu_tixing07 = Button(self.root, font=("黑体",17),text='下一题', width=10,command=self.next,relief=GROOVE)
        self.bu_tixing07.place(relx=.70,rely=.9)
        self.bu_tixing010=Button(self.root,font=("黑体",17),text='提交',width=10,command=self.submit,relief=GROOVE)
        self.bu_tixing010.place(relx=.81,rely=.9)
    def submit(self):
        n=0
        num='' if self.rightorerror.count(0)==0 else self.rightorerror.count(0)
        print(self.rightorerror)
        if  num!='':
            self.boom=askquestion("是|否",f"您还有{num}题未完成")
            if self.boom=='yes':
                book=askquestion("是|否",f"您的得分是{self.grade},是否重新训练")
                if book=='yes':
                    self.build_content()
                else:
                    self.build_menu()

        else:
            self.boom=askquestion("是|否","是否提交")
            if self.boom=='yes':
                book=askquestion("再来一遍|否",f"您的得分是{n},点否退出到主菜单")
                if book=='yes':
                    self.build_content()
                else:
                    self.build_menu()
    def word(self):
        self.content.config(state=NORMAL)
        for i in range(len(self.nowquestion)):
            if self.nowquestion[i:i+13]=='CorrectAnswer' or self.nowquestion[i:i+14]=='Correct Answer':
                self.questionmod=1
                self.analysis = self.nowquestion[i:]
                self.anwser=self.nowquestion[i+14:self.nowquestion[i+13:].find('\n')+i+13]
                # self.up1.set(self.nowquestion[:i])
                self.nowquestion=self.nowquestion.replace('B.','\nB.').replace('C.','\nC.').replace('D.','\nD.')
                self.content.delete("1.0","end")
                self.content.insert("insert",self.nowquestion[:i])
                break
            elif self.nowquestion[i:i+7]=='Answer:':
                # print(self.nowquestion)
                self.questionmod=1
                self.analysis=self.nowquestion[i:]
                self.anwser=self.nowquestion[i+7:self.nowquestion[i:].find('\n')+i]
                # self.up1.set(self.nowquestion[:i])
                self.nowquestion=self.nowquestion.replace('B.','\nB.').replace('C.','\nC.').replace('D.','\nD.')
                self.content.delete("1.0","end")
                self.content.insert("insert",self.nowquestion[:i])
                break
        self.content.config(state=DISABLED)
        print(self.nowquestion)
        print(self.anwser,1)
        # print(self.analysis)
                # print(self.nowquestion[:i])
    def build_gui(self):
        self.build_menu()
        self.build_Main()
    def main(self):
        self.root.mainloop()
if __name__ == '__main__':
    gui = GuessGui('答题系统')
    gui.build_gui()
    gui.main()
