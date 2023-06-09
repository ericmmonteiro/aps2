 private static String namePaginaPrincipal ;
    public TesteAps2() {
    }
    
    
    @BeforeAll
    public static void setUp() {
         System.setProperty("webdriver.chrome.driver", 
	                "C:/Users/fatec.senai/Downloads/trabalho2-1.html");
	        
        
         driver = new ChromeDriver();

        driver.get("C:/Users/fatec.senai/Downloads/trabalho2-1.html");
    
        namePaginaPrincipal = driver.getWindowHandle();
    }
    
    
    
    @Test
    public void testTituloCadastroPessoa(){
      driver.get("C:/Users/fatec.senai/Downloads/trabalho2-1.html");
      String tituloExperado ="Cadastro Pessoa"; 
        
      Assert.assertEquals(tituloExperado,driver.getTitle());
    }
    
     @Test
    public void testeValidaNomeValido(){
    	 
        driver.get("C:/Users/fatec.senai/Downloads/trabalho2-1.html");
        
        WebElement campoNome = driver.findElement(By.id("nome"));
        WebElement salvarButton = driver.findElement(By.id("botao_somar"));
        campoNome.sendKeys("");
		salvarButton.click();

		WebElement resultadoDiv = driver.findElement(By.id("resultado"));
		String resultado = resultadoDiv.getText();
		assertEquals("Preencha o campo nome", resultado);
	}
    
     @Test
 	public void testValidarEndereco() {

 		WebElement nomeInput = driver.findElement(By.id("nome"));
 		WebElement enderecoInput = driver.findElement(By.id("endereco"));
 		WebElement salvarButton = driver.findElement(By.id("botao_somar"));

 	
 		nomeInput.sendKeys("Eric Monteiro");

 		enderecoInput.sendKeys("");
 		salvarButton.click();

 		WebElement resultadoDiv = driver.findElement(By.id("resultado"));
 		String resultado = resultadoDiv.getText();
 		assertEquals("Preencha o campo endereco", resultado);
 	}

 	@Test
 	public void testValidarSexo() {

 		WebElement nomeInput = driver.findElement(By.id("nome"));
 		WebElement enderecoInput = driver.findElement(By.id("endereco"));
 		WebElement sexoSelect = driver.findElement(By.id("sexo"));
 		WebElement salvarButton = driver.findElement(By.id("botao_somar"));

 		
 		nomeInput.sendKeys("Eric");
 		enderecoInput.sendKeys("Rua joao maria 123");

 	
 		sexoSelect.sendKeys("...");
 		salvarButton.click();

 		WebElement resultadoDiv = driver.findElement(By.id("resultado"));
 		String resultado = resultadoDiv.getText();
 		assertEquals("Selecione um valor para o campo sexo", resultado);
 	}

 	@Test
 	public void testValidarIdade() {

 		WebElement nomeInput = driver.findElement(By.id("nome"));
 		WebElement enderecoInput = driver.findElement(By.id("endereco"));
 		WebElement sexoSelect = driver.findElement(By.id("sexo"));
 		WebElement idadeInput = driver.findElement(By.id("idade"));
 		WebElement salvarButton = driver.findElement(By.id("botao_somar"));

 	
 		nomeInput.sendKeys("Eric Monteiro");
 		enderecoInput.sendKeys("Rua Joao Maria 123");
 		sexoSelect.sendKeys("m");

 	
 		idadeInput.sendKeys("");
 		salvarButton.click();

 		WebElement resultadoDiv = driver.findElement(By.id("resultado"));
 		String resultado = resultadoDiv.getText();
 		assertEquals("Preencha o campo idade, somente com numeros", resultado);
 	}

 	@Test
 	public void testValidarTituloPagina() {

 		String tituloPagina = driver.getTitle();
 		assertEquals("Trabalho 2-1", tituloPagina);
 	}

 	@AfterAll
 	public void tearDown() {
 		if (driver != null) {
 			driver.quit();
 		}
 	}
 }
