import streamlit as st

# --- Page Setup ---
st.set_page_config(page_title="ARITHMETIC CALCULATOR 👑", page_icon="🧮")

# --- Session Setup ---
if "expression" not in st.session_state:
    st.session_state.expression = ""

# --- Theme Toggle ---
dark = st.toggle("🌙 Dark Mode", value=True)
bg = "#111" if dark else "#fff"
text_color = "#0f0" if dark else "#000"
btn_color = "#444" if dark else "#ddd"
btn_text = "#fff" if dark else "#000"
op_color = "#e91e63"

# --- Title ---
st.title("🧮 ARITHMETIC CALCULATOR")

# --- Expression Display ---
st.markdown(f"""
<div style='
    background-color: {bg};
    color: {text_color};
    font-size: 32px;
    padding: 15px;
    border-radius: 10px;
    text-align: right;
    border: 2px solid #888;
    margin-bottom: 10px;
'>
    {st.session_state.expression if st.session_state.expression else "0"}
</div>
""", unsafe_allow_html=True)

# --- Button Click Handler ---
def button_click(label):
    if label == "=✅":
        try:
            st.session_state.expression = str(eval(
                st.session_state.expression.replace("×", "*").replace("÷", "/")
            ))
        except:
            st.session_state.expression = "Error"
    elif label == "Clear 🧹":
        st.session_state.expression = ""
    else:
        st.session_state.expression += label.strip()  # Remove any extra space

# --- Buttons Layout (Minimalist with Operator Visibility Fix) ---
buttons = [
    ["7", "8", "9", "÷"],
    ["4", "5", "6", "×"],
    ["1", "2", "3", "-\u00A0"],
    ["Clear 🧹", "0", "=✅", "+\u00A0"]
]

for row in buttons:
    cols = st.columns(len(row))
    for i, label in enumerate(row):
        if cols[i].button(label, key=f"{label}_{i}"):
            button_click(label)
            st.rerun()

# --- Optional Manual Input ---
with st.form("manual_input"):
    expr = st.text_input("Or type an expression:", value=st.session_state.expression)
    submit = st.form_submit_button("Calculate")
    if submit:
        try:
            st.session_state.expression = str(eval(expr.replace("×", "*").replace("÷", "/")))
        except:
            st.session_state.expression = "Error"
        st.rerun()
