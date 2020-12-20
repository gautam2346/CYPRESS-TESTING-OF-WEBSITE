# CYPRESS-TESTING-OF-WEBSITE

describe('MyTestSuite', () => {
    const visit = (darkAppearance) =>
    cy.visit('https://1e20c53ea738.ngrok.io', {
      onBeforeLoad (win) {
        cy.stub(win, 'matchMedia')
        .withArgs('(prefers-color-scheme: dark)')
        .returns({
          matches: darkAppearance,
        })
      },
    })
  
  const verify_button = () => {
    cy.contains('Clear all images')
  }

  const delete_button = () => {
    cy.contains('Generate Image').click()
    cy.contains('Generate Image').click()
    cy.contains('Generate Image').click()
    cy.contains('Clear all images').click()
  }

  const Not_visible_delete_button = () => {
    cy.contains('Clear all images').click()
  }

  const visible_delete_button = () => {
    cy.contains('Generate Image').click()
    cy.contains('Generate Image').click()
    cy.contains('Clear all images').click()
  }

  const text_color_button_light = () => {
    cy.contains('Generate Image').click()
    cy.contains('Clear all images').should('have.css', 'color', 'rgb(220, 53, 69)')
  }

  const text_color_button_dark = () => {
    cy.contains('Generate Image').click()
    cy.contains('Clear all images').should('have.css', 'color', 'rgb(204, 204, 204)')
  }

  const button_color_button_light = () => {
    cy.contains('Generate Image').click()
    cy.contains('Clear all images').should('have.css', 'background-color', 'rgb(243, 243, 243)')
  }

  const button_color_button_dark = () => {
    cy.contains('Generate Image').click()
    cy.contains('Clear all images').should('have.css', 'background-color', 'rgb(220, 53, 69)')
  }

  it('Verify the button- "clear all images" in light mode', function () {
    visit(false)
    verify_button()
  })
  
  it('Verify the button- "clear all images" in dark mode', function () {
    visit(true)
    verify_button()
  })

  it('Verify delete functionality of the button in light mode', function () {
    visit(false)
    delete_button()
  })
  
  it('Verify delete functionality of the button in dark mode', function () {
    visit(true)
    delete_button()
  })

  it('visibility of the button- when there is no generated image in light mode', function () {
    visit(false)
    Not_visible_delete_button()
  })
  
  it('visibility of the button- when there is no generated image in dark mode', function () {
    visit(true)
    Not_visible_delete_button()
  })

  it('visibility of the button- when there is a generated image in light mode', function () {
    visit(false)
    visible_delete_button()
  })
  
  it('visibility of the button- when there is a generated image in dark mode', function () {
    visit(true)
    visible_delete_button()
  })

  it('Verify colour of the text of the button in light mode', function () {
    visit(false)
    text_color_button_light()
  })
  
  it('Verify colour of the text of the button in dark mode', function () {
    visit(true)
    text_color_button_dark()
  })

  it('Verify colour of the button in light mode', function () {
    visit(false)
    button_color_button_light()
  })
  
  it('Verify colour of the button in dark mode', function () {
    visit(true)
    button_color_button_dark()
  })
    
  /*it('Verify the button- clear all images', () => {
        cy.visit('https://761577e26745.ngrok.io')
        cy.contains('Clear all images')
        cy.clearLocalStorage()
    })

    it('Verify delete functionality of the button', () => {
        cy.visit('https://761577e26745.ngrok.io')
        cy.contains('Generate Image').click()
        cy.contains('Generate Image').click()
        cy.contains('Generate Image').click()
        cy.contains('Clear all images').click()
    })

   it('visibility of the button- when there is no generated image', () => {
        cy.visit('https://761577e26745.ngrok.io')
        cy.contains('Clear all images').click()
    })

    it('visibility of the button- when there is a generated image', () => {
        cy.visit('https://761577e26745.ngrok.io')
        cy.contains('Generate Image').click()
        cy.contains('Generate Image').click()
        cy.contains('Clear all images').click()
    })

    it('colour of the text of the button', () => {
        cy.visit('https://761577e26745.ngrok.io')
        cy.contains('Generate Image').click()
        cy.contains('Clear all images').should('have.css', 'color', 'rgb(204, 204, 204)')
    })
    
    it('colour of the button', () => {
        cy.visit('https://761577e26745.ngrok.io')
        cy.contains('Generate Image').click()
        cy.contains('Clear all images').should('have.css', 'background-color', 'rgb(220, 53, 69)')
    })*/        
  })
