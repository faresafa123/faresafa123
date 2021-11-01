 test("Then i click on Action icon modal should be open", ()=>{
      const onNavigate=(pathname)=>{
        document.body.innerHTML=ROUTES({pathname})
      }
      Object.defineProperty(window,'localStorage',{value:localStorageMock})
      window.localStorage.setItem('user',JSON.stringify({
        type:'Employee'
      }))
      const bill=new Bills({
      document,onNavigate,firestore:null,localStorage:window.localStorage})
      const html=BillsUI({data:bills})
      document.body.innerHTML=html
      const icons=screen.getAllByTestId('icon-eye')
      const handleClickIconEye1=jest.fn((e)=>bill.handleClickIconEye(e,icons))
      icons.forEach(icon=>{icon.addEventListener('click',handleClickIconEye1)
      fireEvent.click(icon)
    })
      expect(handleClickIconEye1).toHaveBeenCalled()
    })
  
