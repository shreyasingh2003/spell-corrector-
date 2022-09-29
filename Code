from tkinter import *
from turtle import end_fill
import pandas as pd
from nltk.metrics.distance import jaro_similarity
from sklearn.feature_extraction.text import TfidfVectorizer
data = pd.read_csv("clean_data.csv ")


tf = TfidfVectorizer()
vectors = tf.fit_transform(data["text"])
v = tf.vocabulary_


def corrector2(word):
    sim = [jaro_similarity(word, i) for i in v.keys()]
    
    df = pd.DataFrame.from_dict(probs, orient='index').reset_index()
    df = df.rename(columns={"index":"word", 0 : "probs"})
    df["sim"] = sim
    show = df.sort_values(["sim","probs"], ascending=False).head()
    
    return show

root = tk.Tk()
root.geometry("410x300")  
root.title("Word Predictor + suggestion by Aman and Shreya") 
root.iconbitmap("icon.ico") 
font1=('Times',24,'bold')  
 



l0=tk.Label(text='Autocomplete',font=font1)
l0.grid(row=0,column=0,columnspan=3) 
def my_upd(rootidget):  
    root = rootidget.widget
    index = int(root.curselection()[0]) 
    value = root.get(index)
    load_str.set(value) 
    for row in vocablory:
        if row[1]==value:
  
            break
    l1.delete(0,END)  
def my_down(rootidget): 
    l1.focus() 
    l1.selection_set(0) 
    

vocablory=v
load_str=tk.StringVar() 
inputs=tk.Entry(root,textvariable=load_str,font=font1,width=23)
inputs.grid(row=1,column=0,padx=12,pady=3,sticky='w')

l1 = tk.Listbox(root,height=6,font=font1,relief='flat',width=10,
    bg='SystemButtonFace',highlightcolor= 'SystemButtonFace')
l1.grid(row=2,column=0,padx=50,sticky='w') 

def get_data(*args):
    search_str=inputs.get()
    l1.delete(0,END)
    for element in vocablory.keys():
        if(re.match(search_str,element,re.IGNORECASE)):
            l1.insert(tk.END,element) 

inputs.bind('<Down>', my_down) 
l1.bind('<Right>', my_upd)
l1.bind('<Return>', my_upd)
load_str.trace('w',get_data)  

root.mainloop()

