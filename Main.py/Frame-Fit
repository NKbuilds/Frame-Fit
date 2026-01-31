#hey so this program is a simple one. so ig you guys may have faced problems with your image getting cropped while uploading a linkedin banner or a whatsapp profile pic etc
#this program just solves the problem by centering the image and adding padding.
#you guys can checkout my github:github.com/NKbuilds

#Here the libraries we have used are the pillow library and the tkinter for GUI.

import tkinter as tk
from tkinter import filedialog, messagebox
from PIL import Image
import os

def letterboximg(img,w,h, bgcol):
    origw,origh = img.size
    scalew=w/origw
    scaleh = h / origh
    scl= min(scalew, scaleh)

    neww=int(origw * scl)
    newh = int(origh*scl)

    rsz = img.resize((neww,newh), Image.LANCZOS)

    padl=(w - neww)//2
    padt = (h-newh) // 2

    res=Image.new('RGB',(w,h), bgcol)
    res.paste(rsz, (padl,padt))
    return res


class ImgResizerApp:
    def __init__(self,rt):
        self.rt=rt
        self.rt.title("FRAME FIT")
        self.rt.geometry("550x550")

        tk.Label(rt, text="FRAME FIT",
                 font=("Arial",16, "bold")).pack(pady=20)

        tk.Button(rt,text="SELECT IMAGE",
                  command=self.selinput,
                  width=30,height=2,
                  bg="#2196F3",fg="white",
                  font=("Arial", 11,"bold")).pack(pady=20)

        self.inplbl = tk.Label(rt,text="No file selected", fg="gray")
        self.inplbl.pack(pady=10)

        tk.Label(rt, text="Width:",font=("Arial", 11)).pack()
        self.wentry=tk.Entry(rt, width=20,font=("Arial",11))
        self.wentry.pack(pady=5)
        self.wentry.insert(0,"1080")

        tk.Label(rt,text="Height:", font=("Arial",11)).pack()
        self.hentry = tk.Entry(rt,width=20, font=("Arial", 11))
        self.hentry.pack(pady=5)
        self.hentry.insert(0, "1080")

        tk.Label(rt,text="Padding Color:",font=("Arial", 11)).pack(pady=10)
        self.colvar=tk.StringVar(value="white")
        tk.Radiobutton(rt,text="White", variable=self.colvar,
                       value="white",font=("Arial",10)).pack()
        tk.Radiobutton(rt, text="Black",variable=self.colvar,
                       value="black", font=("Arial", 10)).pack()

        tk.Button(rt, text="RESIZE NOW",
                  command=self.procimg,
                  bg="#4CAF50", fg="white",
                  width=30,height=3,
                  font=("Arial",14, "bold")).pack(pady=30)

        self.inpath=None

    def selinput(self):
        self.inpath=filedialog.askopenfilename(
            title="Select Image",
            filetypes=[("All Images","*.jpg *.jpeg *.png *.bmp *.gif")]
        )

        if self.inpath:
            fname=os.path.basename(self.inpath)
            self.inplbl.config(text=f"Selected: {fname}",fg="green", font=("Arial",10,"bold"))
            print(f"Selected: {self.inpath}")


    def procimg(self):
        print("\n"+"="*50)
        print("STARTING RESIZE PROCESS")
        print("="*50)

        if not self.inpath:
            print("ERROR: No image selected!")
            messagebox.showerror("Error","Please select an image first!")
            return

        try:
            wd=int(self.wentry.get())
            ht = int(self.hentry.get())
            print(f"Target size: {wd} x {ht}")

            padcol=(255,255,255) if self.colvar.get()=="white" else (0, 0,0)
            print(f"Padding: {self.colvar.get()}")

            print(f"Loading: {self.inpath}")
            im=Image.open(self.inpath)
            print(f"Original size: {im.size[0]} x {im.size[1]}")

            if im.mode!='RGB':
                im=im.convert('RGB')

            print("Processing...")
            res=letterboximg(im, wd,ht, padcol)
            print(f"Result size: {res.size[0]} x {res.size[1]}")

            outpath=filedialog.asksaveasfilename(
                title="Save Resized Image As",
                defaultextension=".jpg",
                initialfile="resized_image.jpg",
                filetypes=[("JPEG Image","*.jpg"),("PNG Image", "*.png")]
            )

            if not outpath:
                print("Save cancelled by user")
                messagebox.showinfo("Cancelled","Save operation cancelled.")
                return

            print(f"Saving to: {outpath}")

            if outpath.lower().endswith('.png'):
                res.save(outpath,'PNG')
            else:
                res.save(outpath,'JPEG', quality=95)

            print("SUCCESS!")
            print("="*50)

            outfname=os.path.basename(outpath)
            messagebox.showinfo("SUCCESS!",
                                f"Image saved successfully!\n\n"
                                f"Filename: {outfname}\n\n"
                                f"Original: {im.size[0]} × {im.size[1]}\n"
                                f"Output: {res.size[0]} × {res.size[1]}")

        except Exception as e:
            print(f"ERROR: {e}")
            import traceback
            traceback.print_exc()
            messagebox.showerror("Error",f"Something went wrong:\n\n{str(e)}")

if __name__=="__main__":
    print("Starting Image Resizer...")
    root=tk.Tk()
    app=ImgResizerApp(root)
    root.mainloop()
